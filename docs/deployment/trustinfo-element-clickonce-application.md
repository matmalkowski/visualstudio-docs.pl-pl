---
title: '&lt;trustinfo —&gt; — Element (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d3d683ca2dde02ec63a00f870e1c1b9fd775983f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustinfo —&gt; — Element (aplikacji ClickOnce)
Opisuje minimalne uprawnienia zabezpieczeń wymagane do zastosowania do uruchomienia na komputerze klienckim.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `trustInfo` Element jest wymagany i znajduje się w `asm.v2` przestrzeni nazw. Nie ma żadnych atrybutów, a zawiera następujące elementy.  
  
## <a name="security"></a>zabezpieczenia  
 Wymagany. Ten element jest elementem podrzędnym `trustInfo` elementu. Zawiera on `applicationRequestMinimum` elementu i nie ma żadnych atrybutów.  
  
## <a name="applicationrequestminimum"></a>applicationRequestMinimum  
 Wymagany. Ten element jest elementem podrzędnym `security` element i zawiera `PermissionSet`, `assemblyRequest`, i `defaultAssemblyRequest`elementy. Ten element nie ma żadnych atrybutów.  
  
## <a name="permissionset"></a>PermissionSet  
 Wymagany. Ten element jest elementem podrzędnym `applicationRequestMinimum` element i zawiera `IPermission` elementu. Ten element ma następujące atrybuty.  
  
-   `ID`  
  
     Wymagany. Identyfikuje zestaw uprawnień. Ten atrybut może mieć dowolną wartość. Odwołuje się identyfikator `defaultAssemblyRequest` i `assemblyRequest` atrybutów.  
  
-   `version`  
  
     Wymagany. Identyfikuje wersję uprawnienia. Ta wartość jest zazwyczaj `1`.  
  
## <a name="ipermission"></a>IPermission  
 Opcjonalny. Ten element jest elementem podrzędnym `PermissionSet` elementu. `IPermission` Elementu pełni identyfikuje klasy uprawnień w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. `IPermission` Element ma następujące atrybuty, ale mogą mieć dodatkowe atrybuty, które odpowiadają właściwości klasy uprawnień. Aby sprawdzić składnię określonego uprawnienia, zobacz temat przykłady wymienione w pliku Security.config —.  
  
-   `class`  
  
     Wymagany. Identyfikuje klasy uprawnień przy użyciu silnej nazwy. Na przykład następujący kod identyfikuje `FileDialogPermission` typu.  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
-   `version`  
  
     Wymagany. Identyfikuje wersję uprawnienia. Ta wartość jest zazwyczaj `1`.  
  
-   `Unrestricted`  
  
     Wymagany. Określa, czy aplikacja musi nieograniczony przyznawania to uprawnienie. Jeśli `true`, przyznaj uprawnienie jest bezwarunkowe. Jeśli `false`, lub jeśli zdefiniowano ten atrybut jest ograniczone w zależności od zdefiniowanych atrybutów specyficzne uprawnienia `IPermission` tagu. Wykonaj następujące uprawnienia:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     W tym przykładzie deklaracja <xref:System.Security.Permissions.EnvironmentPermission> ogranicza aplikację do odczytywania tylko zmiennej środowiskowej USERNAME, podczas gdy deklaracja <xref:System.Security.Permissions.FileDialogPermission> daje aplikacji bez ograniczeń użycia wszystkich <xref:System.Windows.Forms.FileDialog> klasy.  
  
## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest  
 Opcjonalny. Określa zestaw uprawnień do wszystkich zestawów. Ten element jest elementem podrzędnym `applicationRequestMinimum` element a ma następującego atrybutu.  
  
-   `permissionSetReference`  
  
     Wymagany. Określa identyfikator zestaw uprawnień będący uprawnienia domyślne. Zestaw uprawnień jest zadeklarowana w `PermissionSet` elementu.  
  
## <a name="assemblyrequest"></a>assemblyRequest  
 Opcjonalny. Określa uprawnienia dla określonego zestawu. Ten element jest elementem podrzędnym `applicationRequestMinimum` element i ma następujące atrybuty.  
  
-   `Name`  
  
     Wymagany. Określa nazwę zestawu.  
  
-   `permissionSetReference`  
  
     Wymagany. Określa identyfikator zestaw uprawnień, który wymaga tego zestawu. Zestaw uprawnień jest zadeklarowana w `PermissionSet` elementu.  
  
## <a name="requestedprivileges"></a>requestedPrivileges  
 Opcjonalny. Ten element jest elementem podrzędnym `security` element i zawiera `requestedExecutionLevel` elementu. Ten element nie ma żadnych atrybutów.  
  
## <a name="requestedexecutionlevel"></a>requestedExecutionLevel  
 Opcjonalny. Określa poziom zabezpieczeń, w którym aplikacja żądań do wykonania. Ten element nie ma elementów podrzędnych i ma następujące atrybuty.  
  
-   `Level`  
  
     Wymagany. Wskazuje, że żąda poziom zabezpieczeń aplikacji. Możliwe wartości to:  
  
     `asInvoker`, żądanie żadne dodatkowe uprawnienia. Ten poziom nie wymaga żadnych dodatkowych zaufania wyświetla monit o.  
  
     `highestAvailable`, żąda uprawnienia najwyższy dostępny dla procesu nadrzędnego.  
  
     `requireAdministrator`, żąda uprawnienia administrator o pełnych uprawnieniach.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje będą instalowane tylko o wartości `asInvoker`. Instalowanie za pomocą innej wartości zakończy się niepowodzeniem.  
  
-   `uiAccess`  
  
     Opcjonalny. Wskazuje, czy aplikacja wymaga dostępu do elementów interfejsu użytkownika chronionych. Wartości są albo `true` lub `false`, a wartość domyślna to false. Tylko podpisane aplikacje powinien mieć wartość true.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja prosi o więcej uprawnień niż komputer kliencki będzie zezwalał na domyślnie języka wspólnego menedżera zaufania w czasie wykonywania będzie monitować użytkownika, jeśli chce udzielić aplikacji tym podwyższonego poziomu zaufania. Jeśli użytkownik nie, aplikacja nie zostanie uruchomiona; w przeciwnym razie będzie uruchamiane z żądanych uprawnień.  
  
 Wszystkie uprawnienia żądana za pomocą `defaultAssemblyRequest` i `assemblyRequest` zostaną przyznane bez monitowania użytkownika, jeśli manifest rozmieszczenia ma prawidłową licencję zaufania.  
  
 Aby uzyskać więcej informacji na temat podniesienia uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md). Aby uzyskać więcej informacji na temat wdrażania zasad, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="examples"></a>Przykłady  
 Kod trzy poniższe przykłady przedstawiają `trustInfo` elementów domyślnych o nazwie strefy zabezpieczeń — Internet, LocalIntranet i FullTrust — do użycia w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia w manifeście aplikacji.  
  
 Pierwszym przykładzie przedstawiono `trustInfo` elementu domyślne uprawnienia dostępne w strefie Internet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 Drugi przykład ilustruje `trustInfo` elementu domyślne uprawnienia dostępne w strefie zabezpieczeń LocalIntranet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 Pokazano w przykładzie trzeci `trustInfo` elementu domyślne uprawnienia dostępne w strefie zabezpieczeń FullTrust.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)