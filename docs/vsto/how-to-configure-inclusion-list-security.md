---
title: 'Porady: Konfigurowanie zabezpieczeń listy dołączania'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e5bd1794b76485d60588b94d3ca139a314f9723
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255840"
---
# <a name="how-to-configure-inclusion-list-security"></a>Porady: Konfigurowanie zabezpieczeń listy dołączania
  Jeśli użytkownik ma uprawnienia administratora, możesz skonfigurować [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufany monit kontroli czy użytkownicy końcowi otrzymują możliwość instalowania rozwiązań pakietu Office przez zapisanie decyzji dotyczącej zaufania lista dołączania. Aby uzyskać informacje o listach dołączania, zobacz [zaufania rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Rozwiązania, znajdujących się we wszystkich pięciu stref można ustawić następujące opcje:  
  
-   Włącz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania monitu o klucz i lista dołączania. Umożliwia użytkownikom udzielenia zaufania do rozwiązań pakietu Office, które są podpisane za pomocą dowolnego certyfikatu.  
  
-   Ogranicz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania monitu o klucz i lista dołączania. Umożliwia użytkownikom końcowym zainstalować rozwiązań pakietu Office, które są podpisane za pomocą certyfikatu, który identyfikuje wydawcę, ale który nie jest zaufany.  
  
-   Wyłącz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania monitu o klucz i lista dołączania. Aby uniemożliwić użytkownikom końcowym zainstalowanie wszelkich rozwiązań pakietu Office, który nie jest podpisany przy użyciu jawnie zaufanych certyfikatów.  
  
## <a name="enable-the-inclusion-list"></a>Włącz listy dołączania  
 Lista dołączania dla strefy należy włączyć użytkownicy końcowi będą widoczne z możliwością instalowania i uruchamiania dowolnego rozwiązania pakietu Office, które pochodzą z tej strefy.  
  
### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Aby włączyć za pomocą Edytora rejestru listy dołączania  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli są one jeszcze nie istnieją, z powiązanymi wartościami.  
  
    |Podklucz wartość ciągu|Wartość|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**wyłączone**|  
    |**Mój komputer**|**włączone**|  
    |**LocalIntranet**|**włączone**|  
    |**TrustedSites:**|**włączone**|  
  
     Domyślnie **Internet** ma wartość **AuthenticodeRequired** i **UntrustedSites** ma wartość **wyłączone**.  
  
### <a name="to-enable-the-inclusion-list-programmatically"></a>Aby programowo włączyć listy dołączania  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C#.  
  
2.  Otwórz *Program.vb* lub *Program.cs* pliku do edycji i Dodaj następujący kod.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Skompiluj i uruchom aplikację.  
  
## <a name="restrict-the-inclusion-list"></a>Ograniczenia dotyczące listy dołączania  
 Lista dołączania należy ograniczyć, tak aby rozwiązań muszą być podpisane przy mają znane tożsamości, zanim użytkownicy są monitowani o decyzji dotyczącej zaufania certyfikatom Authenticode.  
  
### <a name="to-restrict-the-inclusion-list"></a>Ograniczenia dotyczące listy dołączania  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli są one jeszcze nie istnieją, z powiązanymi wartościami.  
  
    |Podklucz wartość ciągu|Wartość|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**wyłączone**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Mój komputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites:**|**AuthenticodeRequired**|  
  
     Domyślnie **Internet** ma wartość **AuthenticodeRequired** i **UntrustedSites** ma wartość **wyłączone**.  
  
### <a name="to-restrict-the-inclusion-list-programmatically"></a>Programowo ograniczenia dotyczące listy dołączania  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C#.  
  
2.  Otwórz *Program.vb* lub *Program.cs* pliku do edycji i Dodaj następujący kod.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Skompiluj i uruchom aplikację.  
  
## <a name="disable-the-inclusion-list"></a>Wyłącz listy dołączania  
 Lista dołączania można wyłączyć, aby użytkownicy końcowi przy użyciu certyfikatu zaufanego i znanego można zainstalować tylko rozwiązania, które są podpisane.  
  
### <a name="to-disable-the-inclusion-list"></a>Aby wyłączyć listy dołączania  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.  
  
2.  Jeśli to nie istnieje, utwórz następujący klucz rejestru:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli są one jeszcze nie istnieją, z powiązanymi wartościami.  
  
    |Podklucz wartość ciągu|Wartość|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**wyłączone**|  
    |**Internet**|**wyłączone**|  
    |**Mój komputer**|**wyłączone**|  
    |**LocalIntranet**|**wyłączone**|  
    |**TrustedSites:**|**wyłączone**|  
  
### <a name="to-disable-the-inclusion-list-programmatically"></a>Aby wyłączyć programowo listy dołączania  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C#.  
  
2.  Otwórz *Program.vb* lub *Program.cs* pliku do edycji i Dodaj następujący kod.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz także  
 [Zaufania rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  