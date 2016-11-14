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

  
 



