# 1. Static Path 관련 설정

### \*\***추후 업데이트 시 static path 관련 설정 부분이 제거될 수 있습니다. 업데이트 후에는 조치하지 않아도 됩니다.\*\***

## Frontend 배포에 사용할 소스코드에는 static path 관련 설정이 필요합니다.

**Frontend 앱 배포 시, url path에 대한 처리가 추가적으로 필요하다는 점을 유의**해야 합니다.\
static 파일들의 경로나 react-router-dom에서 사용하는 path 부분에서 수정이 필요합니다.

위와 같은 조치가 필요한 이유는 배포된 앱에 연결된 외부 URL이 다음과 같은 형식을 갖기 때문입니다.\
Kargo App에 할당된 uid를 바탕으로 외부 URL의 subpath가 결정됩니다.

```sh
https://user-app.krampoline.com/[uid]

ex) https://user-app.krampoline.com/kaw3ge2123sa
```

리액트는 상대 경로 path를 지정할 경우 root domain을 앞에 붙여서 요청을 보냅니다.\
따라서 크램폴린 IDE의 배포 환경에서 단순 상대 경로로 요청을 보내면, 다음과 같이 uid 부분이 제외된 url로 요청을 보냅니다.

```bash
link to '/products' -> https://user-app.krampoline.com/products 
                      (url에 uid가 누락됨)
```

해당 부분에 대한 조치를 위해서는 **Kargo App에 할당된 uid를 포함한 url path를 사용하도록 앱의 전체적인 부분을 변경해야 합니다.**

Kargo App에 할당된 uid 값은 사이드바의 Kargo 탭에서 복사해 올 수 있습니다.\
위에서 복사한 사용자의 uid를 .env 파일에 정의해두고 사용하면 편리합니다.\
**Frontend 앱의 소스코드의 경우 다음의 .env 파일을 포함해서 github 소스 저장소에 push** 해둡니다.

```bash
PUBLIC_URL=/[uid]
REACT_APP_PATH=/[uid]
```

PUBLIC\_URL 값의 경우, index.html에서 기본적인 static 파일들을 서빙할 주소를 지정하는데 사용됩니다.\
자동으로 다음과 같이 지정되어 있으니 추가적인 조치는 불필요합니다.

```html
*** index.html에 자동으로 작성되어 있는 내용입니다. 추가로 수정할 필요가 없습니다.***
<link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
<link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
<link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
```

REACT\_APP\_PATH의 경우 이외에 url path를 사용하는 부분에 대한 작업을 위해서 정의해두었습니다.

먼저 **react-router-dom을 사용한 부분에 대한 조치**가 필요합니다.\
위에서 설명했듯이, 배포 시에는 https://user-app.krampoline.com/\[uid]를 기본 url로 사용해야 합니다.\
따라서 react-router-dom의 Route, Link 등의 컴포넌트가 정상적으로 동작하게 하기 위해서는 /\[uid] 가 모든 url path에 prefix로 붙어야 합니다.

예를 들어 App.js는 아래와 같이 작성해야 합니다.

```javascript
import { BrowserRouter, Routes, Route } from 'react-router-dom';

const staticServerUrl = process.env.REACT_APP_PATH || "";

function App() {
  return (
    <div className="layout">
        <BrowserRouter>
            <Routes>
                {/* 단독 레이아웃 */}
                <Route path={staticServerUrl + "/login"} element={<Login />}></Route>
                <Route path={staticServerUrl + "/signup"} element={<SignUp />}></Route>
                <Route element={<MainLayout />}>
                    <Route path={staticServerUrl + "/"} element={<Main />}></Route>
                    <Route path={staticServerUrl + "/product/:productId"} element={<Detail />}></Route>
                  <Route path="*" element={<NotFound />}></Route>
                </Route>
            </Routes>
        </BrowserRouter>
    </div>
  );
}
```

환경변수에서 가져온 REACT\_APP\_PATH 값을 이용해서 staticServerUrl 변수를 정의하고, Route 컴포넌트에서 url path를 지정하는 곳마다 staticServerUrl를 prefix로 붙여서 지정하고 있습니다.

url path를 지정하는 부분에 대해서는 모두 위와 같은 조치가 필요합니다.

아래의 예시는 react-router-dom의 Link 및 useNavigate를 사용하는 부분입니다.

```javascript
import { Link, useNavigate } from "react-router-dom";

const staticServerUrl = process.env.REACT_APP_PATH || "";

function App() {
const navigate = useNavigate();
  useEffect(() => {
    if (cartItems.length === 0) {
      navigate(staticServerUrl + "/");
    }
  }, [cartItems.length, navigate]);

  return (
    <Col>
      <Link
        to={staticServerUrl + "/product/" + props.product.id}
      >
    </Col>
  );
}
```

다음으로 **window.location.href 에 직접 접근하는 부분에도 해당 조치**가 필요합니다.\
window.location.href 도 url path를 직접 입력하는 것이 필요하므로, static path 설정이 필요합니다. window.location.href 사용 부분을 수정하는 예시는 아래와 같습니다.

```javascript
const staticServerUrl = process.env.REACT_APP_PATH || "";

const alertNeedLogin = () => {
    alert("로그인이 필요합니다.");
    window.location.href = staticServerUrl + "/login";
}
```

만약 **Frontend 레포지토리 내에 static 파일이 존재하고, 이를 image 태그의 src 등으로 참조한다면 마찬가지로 조치가 필요**합니다.\
다음은 public 폴더 내의 cart.png 파일을 참조하는 예시입니다.

```javascript
const staticServerUri = process.env.REACT_APP_PATH || "";

return (
  <header className="header">
    <img src={staticServerUri + "/cart.png"} alt="cart.png" height={30} />
  </header>
)
```

**Backend Server에 요청을 보내는 부분도 마찬가지로 조치가 필요**합니다.\
/\[uid]를 붙이도록 baseUrl을 설정해서 Axios 인스턴스를 생성하고, 이를 이용해서 요청을 보내도록 구성할 수 있습니다.

```javascript
const staticServerUri = process.env.REACT_APP_PATH || "";

const instance = axios.create({
  baseURL:
    staticServerUri + "/api",
  timeout: 1000,
  headers: {
    "Content-Type": "application/json",
  },
});

const getProducts = async () => {
  return await instance.get('/products');
};
```