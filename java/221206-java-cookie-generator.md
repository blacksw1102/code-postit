# CookieGenerator

Helper class / for cookie generation, / carrying cookie descriptor settings / as bean properties / and being able to add and remove cookie / to/from a given response.

**쿠키생성을 위한 헬퍼 클래스로서, bean 프로퍼티로 쿠키 세팅값들을 전달하고거나 response에서 쿠키값을 추가하거나 제거할 수 있다.**

Can serve / as base class / for components / that generate specific cookies / ,such as CookieLocaleResolver and CookieThemeResolver

**특정 쿠키를 생성하는 base 클래스를 컴포넌트들을 위해 제공할 수 있다. CookieLocalResolver나 CookieThemeResolver처럼.**

## setCookiePath

Use the given path / for cookies / created by this generator. The cookie is only visible / to URLs in this path / and below.

**쿠키의 경로를 지정하는데 사용한다. 쿠키는 지정된 경로나 그 하위 경로에서만 활성화 된다.**

## setCookieMaxAge

Use the given maximum age (in seconds) / for cookies / created by this generator. / Useful special value: -1 ... not persistent, / deleted when client shuts down. / Default is no specific maximum age at all, / using the Servlet container's

**쿠키에 유효기간을 지정할 수 있다. 유효기간을 -1 값으로 지정하면 클라이언트가 종료될 때 쿠키가 삭제된다. 기본값일 경우에는 따로 맥시멈 유효기간이 지정되지는 않는다.**

---

### sample

```
public void addCookie(HttpServletRequest response) {
  CookieGenerator cg = new CookieGenerator();
  cg.setCookieName("view");
  cg.setCookiePath("/");
  cg.setCookieMaxAge(60 * 60 * 24);
  cg.addCookie(response, "value");
}
```
