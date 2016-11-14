## web.xml
    <display-name>Struts2</display-name>

    <filter>
        <filter-name>struts2</filter-name>
        <filter-class>org.apache.struts2.dispatcher.FilterDispatcher</filter-class>
    </filter>

    <filter-mapping>
        <filter-name>struts2</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>


## [struts.xml]
    <?xml version="1.0" encoding="UTF-8" ?>

    <!DOCTYPE struts PUBLIC
    "-//Apache Software Foundation//DTD Struts Configuration 2.0//EN"
    "http://struts.apache.org/dtds/struts-2.0.dtd">

    <struts>
    </struts>


## struts.properties 		
		#인코딩 문자체계를 설정한다.
		struts.i18n.encoding=euc-kr (디폴트:UTF-8)		

		#액션의 확장자를 지정한다. 쉼표로 여러 개를 지정할 수 있다.
		struts.action.extension=action (디폴트:action)

		#URL에서 액션 메소드를 지정할 수 있도록 설정한다.
		#'액션!메소드.action' 또는 '액션.action?method=메소드'
		struts.enable.DynamicMethodInvocation=false (디폴트:true)

		#개발 타임시 설정한다. 다음 두 가지를 포함한다.
		#struts.i18n.reload=true
		#struts.configuration.xml.reload=true
		struts.devMode=true (디폴트:false)


## struts.xml
    <struts>
    <constant name="struts.i18n.encoding" value="euc-kr"/>
    <constant name="struts.action.extension" value="action"/>
    <constant name="struts.enable.DynamicMethodInvocation" value="true" />
    <constant name="struts.devMode" value="true" />
    </struts>


## Interceptor
#### extends AbstractInterceptor { }
+ com.opensymphony.xwork2.interceptor.AbstractInterceptor
+ intercept() 메소드 오버라이드 (필수)

#### implements Interceptor { }
+ public void init() : 웹 애플리케이션이 deploy 될 때 한 번 실행
+ public String intercept(ActionInvocation invocation) : 요청시 마다 실행
+ public void destroy() : (실행 되지 않음)

#### extends MethodFilterInterceptor { }
+ com.opensymphony.xwork2.interceptor.MethodFilterInterceptor
+ 인터셉터 <적용 제외> 또는 적용 메소드를 지정할 수 있
+ doIntercept() 메소드 오버라이드 (필수)


## implements ServletRequestAware {}
    //ServetRequestAware 구현
    private HttpServletRequest request;
    public void setServletRequest(HttpServletRequest request) {
    this.request = request;
	
	
	

 
 
 
  
+ chain
    -Action들을 chaining 할 때 사용
+ dispatcher
    -View로 forwarding 할 때 사용
+ freemarker
    -FreeMarker 템플릿 엔진을 사용하여 화면을 구성할 때 사용
+ httpheader
    -응답 헤더를 구성할 때 사용
+ redirect
    -다른 URL의 View로 redirct 할 때 사용
+ redirectAction
    -다른 액션으로 redirect  할 때 사용
+ stream
    -파일을 다운로드할 때 사용
+ velocity
    -Velocity 템플릿 엔진을 사용하여 화면을 구성할 때 사용
+ xslt
    -XML을 XSLT와 결합 할 때 사용
+ plainText
    -페이지의 내용을 문자 그대로 보여줄 때 사용

  
# 스트럿츠2에서 세션 받아오기
- 스트럿츠2에서는 세션 데이터을 맵으로 관리하기 때문에 받아올때에도 다음과 같이 맵객체에 담아준다.
    ActionContext con = ActionContext.getContext();
    Map session = con.getSession();  
 
### 세션에 내용을 입력할 경우
- map에 데이터를 넣는 것과 동일하다. 키값으로는 object를 사용해도 된다.
    session.put( "키값" , 내용 );  
 
### 현재 무슨 세션이 있는지 알고자 할 경우

1. 키 값을 알고 있는 경우
- key값을 알고 있을경우에는 key값으로 바로 가져오면 된다.
    Object value = session.get("키값");  

2. 키 값을 모르고 있는 경우
- key값을 모르는 경우에는 세션에 존재하는 모든 키값을 가져와서 해당 데이터를 몽땅 가져온다.
    Set set = session.keySet();
    Iterator ite = set.iterator();
    while(ite.hasNext())
    {
     String key = (String) ite.next();
     Object value = session.get(key);
    }  

### 세션 삭제하기
- session에서 해당 키값에 해당하는 데이터를 제거합니다.
    session.remove("키값");  
 
### JSP 문서에서 세션 확인하기
- if문 사이에 세션을 확인하는 코드를 넣어줍니다.
    <%@ taglib prefix="s" uri="/struts-tags" %>
    <s:if test="#session">
    <!--세션 확인 하는 코드-->
    </s:if>  



