---
title: '&lt;Polecenia&gt; elementu (programu inicjującego) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac3ae61012bec5f8134a48714678110951c03b76
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566202"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Polecenia&gt; elementu (programu inicjującego)
`Commands` Testy opisanego przez elementy podrzędne implementuje element `InstallChecks` elementu i oświadcza, które pakiety [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programu inicjującego należy zainstalować, jeśli test zakończy się niepowodzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `Commands` Element jest wymagany. Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Reboot`|Opcjonalna. Określa, czy jeśli żadnych pakietów, zwróci kod zakończenia ponownego uruchomienia komputera należy ponownie uruchomić system. Na poniższej liście przedstawiono prawidłowe wartości:<br /><br /> `Defer`. Ponowne uruchomienie jest odroczona do przyszłości.<br /><br /> `Immediate`. Powoduje natychmiastowego ponownego uruchomienia, jeśli jeden z pakietów zwrócony kod zakończenia ponownego uruchomienia.<br /><br /> `None`. Powoduje, że żądania ponownego uruchomienia mają być ignorowane.<br /><br /> Wartość domyślna to `Immediate`.|  
  
## <a name="command"></a>Polecenie  
 `Command` Element jest elementem podrzędnym `Commands` elementu. A `Commands` element może mieć co najmniej jeden `Command` elementów. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`PackageFile`|Wymagana. Nazwa pakietu do zainstalowania należy co najmniej jeden z warunków określonych przez `InstallConditions` zwróci wartość false. Pakiet musi być zdefiniowana w tym samym pliku przy użyciu `PackageFile` elementu.|  
|`Arguments`|Opcjonalna. Zestaw argumenty wiersza polecenia do przekazania do pliku pakietu.|  
|`EstimatedInstallSeconds`|Opcjonalna. Szacowany czas w sekundach, trwa instalowanie pakietu. Ta wartość określa rozmiar paska postępu, który inicjujący wyświetla dla użytkownika. Wartość domyślna to 0, w którym to przypadku nie razem, gdy określono szacowania.|  
|`EstimatedDiskBytes`|Opcjonalna. Szacowana ilość miejsca na dysku, w bajtach, które pakiet zajmie się po zakończeniu instalacji zostało ukończone. Ta wartość jest używana w dysk twardy wymagań dotyczących miejsca inicjujący wyświetla dla użytkownika. Wartość domyślna to 0, w przypadku inicjujący nie wyświetla żadnych wymagań dotyczących miejsca na dysku twardym.|  
|`EstimatedTempBytes`|Opcjonalna. Szacowana kwota tymczasowego miejsca w bajtach, które będą wymagać pakietu.|  
|`Log`|Opcjonalna. Ścieżka do pliku dziennika, który generuje pakietu, względem katalogu głównego pakietu.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions` Element jest elementem podrzędnym `Command` elementu. Każdy `Command` element może mieć co najwyżej jeden `InstallConditions` elementu. Jeśli nie `InstallConditions` istnieje element określony przez pakiet `Condition` zawsze uruchamiane.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf` Element jest elementem podrzędnym `InstallConditions` elementu oraz opis dodatnią warunek, pod którym nie mają zostać wykonane polecenie. Każdy `InstallConditions` element może mieć wartość zero lub więcej `BypassIf` elementów.  
  
 `BypassIf` ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagana. Nazwa właściwości do testowania. Właściwość musi wcześniej zostały zdefiniowane przez element podrzędny `InstallChecks` elementu. Aby uzyskać więcej informacji, zobacz [ \<InstallChecks > elementu](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Wymagana. Typ porównania do wykonania. Na poniższej liście przedstawiono prawidłowe wartości:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Wymagana. Wartość do porównania z właściwością.|  
|`Schedule`|Opcjonalna. Nazwa `Schedule` znacznik definiujący, kiedy należy ocenić tę regułę.|  
  
## <a name="failif"></a>FailIf  
 `FailIf` Element jest elementem podrzędnym `InstallConditions` elementu oraz opis dodatnią warunku, pod którym instalacja powinna zostać przerwana. Każdy `InstallConditions` element może mieć wartość zero lub więcej `FailIf` elementów.  
  
 `FailIf` ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagana. Nazwa właściwości do testowania. Właściwość musi wcześniej zostały zdefiniowane przez element podrzędny `InstallChecks` elementu. Aby uzyskać więcej informacji, zobacz [ \<InstallChecks > elementu](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Wymagana. Typ porównania do wykonania. Na poniższej liście przedstawiono prawidłowe wartości:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Wymagana. Wartość do porównania z właściwością.|  
|`String`|Opcjonalna. Tekst do wyświetlenia po awarii.|  
|`Schedule`|Opcjonalna. Nazwa `Schedule` znacznik definiujący, kiedy należy ocenić tę regułę.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes` Element jest elementem podrzędnym `Command` elementu. `ExitCodes` Elementu zawiera jeden lub więcej `ExitCode` elementów, które określają, co należy wykonać instalację w odpowiedzi kod zakończenia z pakietem. Może istnieć jeden opcjonalny `ExitCode` element poniżej `Command` elementu. `ExitCodes` Nie ma żadnych atrybutów.  
  
## <a name="exitcode"></a>exitCode  
 `ExitCode` Element jest elementem podrzędnym `ExitCodes` elementu. `ExitCode` Określa instalację zrobić w odpowiedzi kod zakończenia z pakietem. `ExitCode` nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Value`|Wymagana. Wartość kodu zakończenia, do której należy `ExitCode` element ma zastosowanie.|  
|`Result`|Wymagana. Sposób instalacji powinny reagować na ten kod zakończenia. Na poniższej liście przedstawiono prawidłowe wartości:<br /><br /> `Success`. Flagi za pomyślnie zainstalowanym pakietem.<br /><br /> `SuccessReboot`. Flagi za pomyślnie zainstalowanym pakietem i instruuje ponownego uruchomienia systemu.<br /><br /> `Fail`. Flagi pakietu, ponieważ nie powiodło się.<br /><br /> `FailReboot`. Flagi pakietu, ponieważ nie powiodło się i instruuje ponownego uruchomienia systemu.|  
|`String`|Opcjonalna. Wartość do użytkownika w odpowiedzi na ten kod zakończenia.|  
|`FormatMessageFromSystem`|Opcjonalna. Określa, czy użyć dostarczane przez system błąd odpowiadający kod zakończenia lub wartość podana w `String`. Prawidłowe wartości to `true`, co oznacza, że do użycia dostarczane przez system błąd i `false`, co oznacza, że użyć ciągu podał `String`. Wartość domyślna to `false`. Jeśli ta właściwość jest `false`, ale `String` nie jest ustawiony dostarczane przez system błąd będą używane.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje polecenia dotyczące instalowania programu .NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Produkt i pakiet — odwołanie do schematu](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > — Element](../deployment/installchecks-element-bootstrapper.md)