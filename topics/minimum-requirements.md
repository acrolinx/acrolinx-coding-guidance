# Minimum Requirements to Pass Certification

1) The **customer or partner signed** the **contract**. See [Steps for Building an Integration](https://support.acrolinx.com/hc/en-us/articles/10210859042066-Process-for-Building-an-Integration)
2) The integration doesn't violate the **Acrolinx license model**. (Demo / Questions)
3) Did you **hard-code** the correct **signature**? (Demo / Source)
   + How to set the signature:
      * Sidebar: [JS](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/config.js#L29),
      [Java](https://github.com/acrolinx/acrolinx-sidebar-demo-java/blob/c32678dec4cfd849cc9d33e78fab2ace2bb1de0a/demo/swing/src/main/java/com/acrolinx/client/sidebar/demo/swing/AcrolinxDemoClientSwing.java#L40),
      [.NET (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet#configuration)
      [(2)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/master/Acrolinx.Demo.Sidebar/MultiSample.Designer.cs#L144),
      [C++](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L115)
      * Automated: [Platform API](https://acrolinxapi.docs.apiary.io/#introduction/general-headers/signature),
      [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/test/integration-server/acrolinx-endpoint.test.ts#L65),
      [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L191),
      [.NET](https://github.com/acrolinx/sdk-dotnet/blob/dc346b53ee3b274ecfd40dfe5e4af4855fea4695/Acrolinx.Net/Acrolinx.Net.Tests/TestEnvironment.cs#L26),
      [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/tests/AcrolinxEndpointTest.php#L60)
4) Version information is in place to enable Acrolinx Support. (Demo / Source)
   + How to set the version:
      * Sidebar: [JS](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/config.js#L67),
      [Java](https://github.com/acrolinx/acrolinx-sidebar-demo-java/blob/c32678dec4cfd849cc9d33e78fab2ace2bb1de0a/demo/swing/src/main/java/com/acrolinx/client/sidebar/demo/swing/AcrolinxDemoClientSwing.java#L38),
      [.NET](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/d7194416157e3661fbce8c5473a7bae14059e041/Acrolinx.Demo.Sidebar/Integration.cs#L52)
      (defaults to assembly version),
      [C++](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L125)
      * Automated: [Platform API](https://acrolinxapi.docs.apiary.io/#introduction/general-headers/signature),
      [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/test/integration-server/acrolinx-endpoint.test.ts#L66),
      [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L191),
      [.NET](https://github.com/acrolinx/sdk-dotnet/blob/2655e198e13fa05e7ba8bd3a15b221223e5f4ce7/Acrolinx.Net/Acrolinx.Net/AcrolinxEndpoint.cs#L61)
      (defaults to assembly version),
      [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/src/AcrolinxEndpoint.php#L96)
5) Did you use the correct **Acrolinx branding**? (Demo)
6) The integration seems to be **usable**. (Demo / Questions)
7) The integration uses the best [checking features](checking-features.md) to satisfy the use case. (Demo / Questions)
8) Did you use the correct [authentication mode](configuration.md#authentication)? (Demo / Source)
   + How can the customer set or change the sign-in option?
      * Sidebar: All versions of interactive sign-in: Enterprise Federated Authentication, external authentication, and
        Acrolinx Sign-in work out-of-the-box. [JS (SSO)](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/config.js#L61)
      * Automated:
         + Interactive: [Platform API](https://github.com/acrolinx/platform-api#getting-an-access-token-with-acrolinx-sign-in),
           [JS](https://github.com/acrolinx/sdk-js/blob/217ea70387d8f20f74b3fff1e61addd97699f3ac/test/unit/signin.test.ts#L108),
           [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/SignInInteractiveTest.java#L44),
           [.NET](https://github.com/acrolinx/sdk-dotnet/blob/2655e198e13fa05e7ba8bd3a15b221223e5f4ce7/Acrolinx.Net/Acrolinx.Net.Tests/EndpointTest.cs#L115)
         + SSO: [Platform API](https://acrolinxapi.docs.apiary.io/#reference/authentication-api/requestvalidate-an-api-token),
           [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/test/integration-server/acrolinx-endpoint.test.ts#L149),
           [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/SignInSsoTest.java#L32),
           [.NET](https://github.com/acrolinx/sdk-dotnet/blob/dc346b53ee3b274ecfd40dfe5e4af4855fea4695/Acrolinx.Net/Acrolinx.Net.Tests/EndpointTest.cs#L60),
           [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/tests/AcrolinxEndpointTest.php#L122)
         + API token: [Platform API (1)](https://acrolinxapi.docs.apiary.io/#introduction/general-headers/access-token)
           [(2)](https://github.com/acrolinx/platform-api#getting-an-api-token),
           [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/test/integration-server/acrolinx-endpoint.test.ts#L185),
           [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L193),
           [.NET](https://github.com/acrolinx/sdk-dotnet/blob/2655e198e13fa05e7ba8bd3a15b221223e5f4ce7/Acrolinx.Net/Acrolinx.Net.Tests/EndpointTest.cs#L261)
9) Did you set the correct [check type](check-types.md)? (Demo / Source / Questions)
    + How to set the check type:
      * Sidebar: always `interactive`
      * Automated: [Platform API](https://acrolinxapi.docs.apiary.io/#reference/checking-api/submit-a-check/submit-a-check),
      [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/src/check.ts#L64),
      [Java (1)](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L237)
      [(2)](https://acrolinx.github.io/sdk-java/com/acrolinx/client/sdk/check/CheckOptionsBuilder.html#withCheckType-com.acrolinx.client.sdk.check.CheckType-),
      [.NET](https://github.com/acrolinx/sdk-dotnet/blob/20ca7d1e7d58caf5f60cba33dbca72d7700e39ae/Acrolinx.Net/Acrolinx.Net/Check/CheckOptions.cs#L30),
      [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/tests/AcrolinxEndpointTest.php#L274)
10) The [Acrolinx URL](configuration.md#acrolinx-url):
    + Isn't hardcoded
    + Doesn't default to `https://partner-dev.internal.acrolinx.sh/`.

    Ideally, an admin can configure the Acrolinx URL for all users. (Demo / Source / Questions)
    + How to set the Acrolinx URL and enable or disable the Sidebar Start Page:
      * Sidebar: [JS (1)](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/config.js#L28)
      [(2)](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/config.js#L57),
      [Java (1)](https://acrolinx.github.io/sidebar-sdk-java/com/acrolinx/sidebar/pojo/settings/AcrolinxSidebarInitParameter.AcrolinxSidebarInitParameterBuilder.html#withServerAddress-java.lang.String-)
      [(2)](https://acrolinx.github.io/sidebar-sdk-java/com/acrolinx/sidebar/pojo/settings/AcrolinxSidebarInitParameter.AcrolinxSidebarInitParameterBuilder.html#withShowServerSelector-java.lang.Boolean-),
      [.NET (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/d7194416157e3661fbce8c5473a7bae14059e041/Acrolinx.Demo.Sidebar/Integration.cs#L40)
      [(2)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/d7194416157e3661fbce8c5473a7bae14059e041/Acrolinx.Demo.Sidebar/Integration.cs#L41),
      [C++ (1)](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L108)
      [(2)](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L109)
      * Automated:
      [Platform API (1)](https://github.com/acrolinx/platform-api#getting-started)
      [(2)](https://acrolinxapi.docs.apiary.io/#introduction/general-headers/base-url),
      [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/test/integration-server/acrolinx-endpoint.test.ts#L62),
      [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L191),
      [.NET](https://github.com/acrolinx/sdk-dotnet/blob/dc346b53ee3b274ecfd40dfe5e4af4855fea4695/Acrolinx.Net/Acrolinx.Net.Tests/TestEnvironment.cs#L27),
      [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/tests/AcrolinxEndpointTest.php#L53)
11) You set the correct [format](text-extraction.md#check-format-and-supporting-multiformat-editors).
  Ideally, use the `auto` setting.
  Usually, everything that is displayed in the UI. Sometimes additional custom fields. (Demo / Source)
    + How to set the content format:
      * Sidebar: [JS (1)](https://acrolinx.github.io/sidebar-sdk-js/pluginDoc/interfaces/adapterinterface.html#getformat),
      [Java (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-java/blob/c32678dec4cfd849cc9d33e78fab2ace2bb1de0a/demo/jfx/src/main/java/com/acrolinx/client/sidebar/demo/jfx/AcrolinxJFXIntegration.java#L34)
      [(2)](https://acrolinx.github.io/sidebar-sdk-java/com/acrolinx/sidebar/InputAdapterInterface.html#getInputFormat--),
      [.NET (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/79ee2e363ac4bc51e1d6e9d9572660a31cf4da5f/Acrolinx.Demo.Sidebar/Integration.cs#L79)
      [(2)](https://github.com/acrolinx/sidebar-sdk-dotnet/blob/667d774265fa48f230cc751c79c1ba0a7fa64515/Acrolinx.Sidebar/Documents/IDocument.cs#L11),
      [C++](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L140)
      * Automated: [Platform API](https://acrolinxapi.docs.apiary.io/#reference/checking-api/submit-a-check/submit-a-check),
      [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/src/check.ts#L67),
      [Java](https://acrolinx.github.io/sdk-java/com/acrolinx/client/sdk/check/CheckOptionsBuilder.html#withContentFormat-java.lang.String-),
      [.NET](https://github.com/acrolinx/sdk-dotnet/blob/dc346b53ee3b274ecfd40dfe5e4af4855fea4695/Acrolinx.Net/Acrolinx.Net.Tests/EndpointTest.cs#L151),
      [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/tests/AcrolinxEndpointTest.php#L275)
12) You provided a recognizable [reference](text-extraction.md#Enable-Acrolinx-Providing-Guidance-and-Analytics).
    (Demo / Source / Questions)
    + How to set the content reference:
      * Sidebar: [JS (1)](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/config.js#L33)
      (defaults to window location)
      [(2)](https://acrolinx.github.io/sidebar-sdk-js/pluginDoc/interfaces/successfulcontentextractionresult.html#documentreference),
      [Java (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-java/blob/c32678dec4cfd849cc9d33e78fab2ace2bb1de0a/demo/jfx/src/main/java/com/acrolinx/client/sidebar/demo/jfx/AcrolinxJFXIntegration.java#L34)
      [(2)](https://acrolinx.github.io/sidebar-sdk-java/com/acrolinx/sidebar/InputAdapterInterface.html#getDocumentReference--),
      [.NET (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/79ee2e363ac4bc51e1d6e9d9572660a31cf4da5f/Acrolinx.Demo.Sidebar/Integration.cs#L87)
      [(2)](https://github.com/acrolinx/sidebar-sdk-dotnet/blob/667d774265fa48f230cc751c79c1ba0a7fa64515/Acrolinx.Sidebar/Documents/IDocument.cs#L12),
      [C++](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L140)
      * Automated: [Platform API](https://acrolinxapi.docs.apiary.io/#reference/checking-api/submit-a-check/submit-a-check),
      [JS (1)](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/examples/check.ts#L50)
      [(2)](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/src/check.ts#L73),
      [Java (1)](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L212)
      [(2)](https://acrolinx.github.io/sdk-java/com/acrolinx/client/sdk/check/CheckRequestBuilder.html#withContentReference-java.lang.String-),
      [.NET](https://github.com/acrolinx/sdk-demo-dotnet/blob/17b73231e7f3e1fc6286ab8b6549281f1f0ee70c/Acrolinx.Net.Demo/Program.cs#L41),
      [PHP](https://github.com/acrolinx/sdk-php/blob/21d976471d389f3ea8b9175ce70b26b3588fa4b3/tests/AcrolinxEndpointTest.php#L282)
13) The [content](text-extraction.md#structure) is well structured and includes all necessary content.
  Usually, everything that's displayed in the UI. Sometimes additional custom fields. (Demo / Source)
    + How to set the structure of the content:
      * Sidebar: [JS (1)](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/multi-editor.html#L80)
      [(2)](https://github.com/acrolinx/acrolinx-sidebar-demo/blob/d49f8e5fc22d6ddaef033ccfacdba30d91ced9e2/samples/multi-editor.html#L93),
      [Java (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-java/blob/c32678dec4cfd849cc9d33e78fab2ace2bb1de0a/demo/jfx/src/main/java/com/acrolinx/client/sidebar/demo/jfx/AcrolinxJFXIntegration.java#L34)
      [(2)](https://acrolinx.github.io/sidebar-sdk-java/com/acrolinx/sidebar/InputAdapterInterface.html#getContent--),
      [.NET (1)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/79ee2e363ac4bc51e1d6e9d9572660a31cf4da5f/Acrolinx.Demo.Sidebar/Integration.cs#L79)
      [(2)](https://github.com/acrolinx/acrolinx-sidebar-demo-dotnet/blob/79ee2e363ac4bc51e1d6e9d9572660a31cf4da5f/Acrolinx.Demo.Sidebar/Integration.cs#L76)
      [(3)](https://github.com/acrolinx/sidebar-sdk-dotnet/blob/667d774265fa48f230cc751c79c1ba0a7fa64515/Acrolinx.Sidebar/Util/Adapter/IAdapter.cs#L14),
      [C++ (1)](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L140)
      [(2)](https://github.com/acrolinx/sidebar-demo-cpp/blob/064939fbfbe2e4b238ab9250b1568a3d91475382/Acrolinx.Adapter.Demo.Sidebar.Cpp/Acrolinx.Adapter.Demo.Sidebar.CppDlg.cpp#L141)
      * Automated: [Platform API](https://acrolinxapi.docs.apiary.io/#reference/checking-api/submit-a-check/submit-a-check),
      [JS](https://github.com/acrolinx/sdk-js/blob/2d6436f9b994137a646bcaed69ba70e04ec9e765/src/check.ts#L53),
      [Java](https://github.com/acrolinx/sdk-java/blob/127d42a5247e4e52d72ce829b649befbfb2eeffd/src/test/java/com/acrolinx/client/sdk/integration/CheckTest.java#L118),
      [.NET](https://github.com/acrolinx/sdk-dotnet/blob/dc346b53ee3b274ecfd40dfe5e4af4855fea4695/Acrolinx.Net/Acrolinx.Net.Tests/EndpointTest.cs#L148),
      [PHP](https://github.com/acrolinx/sdk-php/blob/81d8d6e6f3fa17f53299b2af923f4d86045d5d4b/tests/AcrolinxEndpointTest.php#L280)
14) No obvious security issues are present. (Demo / Questions)
15) The integration can connect to an Acrolinx instance such as `https://partner-dev.internal.acrolinx.sh/`.
    (Demo / Questions)
16) Did you implement a good [scheduling](scheduling.md) mechanism? (Questions)

## See Also

* [Certification Meeting](support.md#Certification-Meeting)
* [Request Validator](https://support.acrolinx.com/hc/en-us/articles/10220886837522-How-To-Use-the-Request-Validator)
