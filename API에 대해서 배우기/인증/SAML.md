# SAML 😼

**SAML**(Security Assertion Markup Language)은 인증 정보 제공자(identity provider)와 서비스 제공자(service provider) 간의 인증 및 인가 데이터를 교환하기 위한 XML 기반의 개방형 표준 데이터 포맷이다. SAML은 SSO(Single Sign-On)를 구현하는 한 가지 방법이다.

<br>

**SAML의 3가지 역할**

1. 주체 (일반적으로 사용자)
2. 인증 정보 제공자 (identity provider, IdP)
3. 서비스 제공자 (service provider, SP)

SAML 사용 예에서 주체는 서비스를 서비스 제공자로부터 요청한다. 이 서비스 제공자는 식별 어서션(assertion)을 인증 정보 제공자로부터 요청하여 가져온다. 이 어서션(assertion)에 기초하여, 서비스 제공자는 접근 제어 결정을 할 수 있다. 즉, 연결된 주체에 대해 일부 서비스를 수행할지의 여부를 결정할 수 있다.



### SAML 공급자? 😲

SAML 용어에서 공급자(Provider)는 시스템에서 사용자가 원하는 서비스에 접속할 수 있도록 도와주는 개체다(일반적으로 서버나 컴퓨터를 의미한다). SAML 서비스를 제공하거나 사용하는 시스템을 일컫는데, 가장 중요한 서비스 공급자는 ID 공급자(identity provider)다.

ID 공급자는 시스템 내 개체로, 실제로 사용자가 자신이 주장하는 사람인지 확인한다. 즉, 인증을 제공한다. 또한 사용자가 시스템의 다양한 개체를 통해 접속할 권한이 있는 서비스인지를 결정할 수 있다. SAML 표준에 따라 인증 서비스를 제공할 수 있는 다양한 구현이 있다.



### assertion? 그게 뭐지? 🙄

SAML 어설션(assertion)은 지금까지 얘기한 모든 정보가 한 컴퓨터에서 다른 컴퓨터로 전송되는 XML 문서다. ID 공급자가 말하는 사람이고 자신이 관심있는 콘텐츠나 서비스에 접속할 권한이 있다고 결정하면 SAML 어설션을 서버에 보내 실제로 해당 서비스를 제공할 수 있다. SAML 어설션은 향상된 보안을 위해 암호화할 수 있다.



[참고1](https://ko.wikipedia.org/wiki/SAML)

[참고2](http://www.itworld.co.kr/news/108736)