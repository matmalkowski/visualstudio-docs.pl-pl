---
title: 'Porady: Konfigurowanie zachowania monitu o zaufanie ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d37e5fa465a5e19b1bfb7577f6ab06c61782f775
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Porady: konfigurowanie funkcji zaufanego monitowania technologii ClickOnce
Możesz określić wiersz zaufania ClickOnce do formantu, czy użytkownicy końcowi otrzymują możliwość instalowania aplikacji ClickOnce, takie jak aplikacje systemu Windows Presentation Foundation, aplikacje konsoli, przeglądarce WPF w aplikacji formularzy systemu Windows aplikacje i rozwiązań pakietu Office. Możesz skonfigurować wiersz zaufania poprzez ustawienie kluczy rejestru na komputerze użytkownika końcowego.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji, które mogą być stosowane do każdej ze stref pięć (Internet, UntrustedSites Mój komputer, LocalIntranet i TrustedSites:).  
  
|Opcja|Wartość ustawienia rejestru|Opis|  
|------------|----------------------------|-----------------|  
|Włącz wiersza zaufania.|`Enabled`|Wiersz zaufania ClickOnce jest wyświetlana tak, aby użytkownicy końcowi mogą udzielać dostępu zaufania dla aplikacji ClickOnce.|  
|Ogranicz wiersza zaufania.|`AuthenticodeRequired`|Tylko zostanie wyświetlony monit zaufania ClickOnce, jeśli ClickOnce — aplikacje są podpisane za pomocą certyfikatu, który identyfikuje wydawcy.|  
|Wyłącz wiersz zaufania.|`Disabled`|Wiersz zaufania ClickOnce jest wyświetlana tylko dla aplikacji ClickOnce, które nie są podpisane za pomocą jawnie zaufanych certyfikatów.|  
  
 W poniższej tabeli przedstawiono domyślne zachowanie dla każdej strefy. Kolumna aplikacji odwołuje się do aplikacji formularzy systemu Windows, aplikacje systemu Windows Presentation Foundation WPF aplikacji przeglądarki i aplikacje konsoli.  
  
|strefy|Aplikacje|rozwiązania pakietu Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Te ustawienia można zastąpić przez włączenie, ograniczenie lub wyłączenie wiersza zaufania ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Włączanie monitowania zaufania ClickOnce  
 Jeśli chcesz, aby użytkownicy końcowi będą widoczne z możliwością Instalowanie i uruchamianie dowolnej aplikacji ClickOnce, która pochodzi z tej strefy, należy włączyć wiersz zaufania dla strefy.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby włączyć wiersz zaufania ClickOnce za pomocą Edytora rejestru  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz `regedit32`, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli są one jeszcze nie istnieją, z powiązanymi wartościami, które przedstawiono w poniższej tabeli.  
  
    |Podklucz wartość ciągu|Wartość|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Dla rozwiązań pakietu Office `Internet` ma wartości domyślnej `AuthenticodeRequired` i `UntrustedSites` ma wartość `Disabled`. Dla wszystkich innych `Internet` ma wartości domyślnej `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Aby programowo włączyć wiersza zaufania ClickOnce  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C# w programie Visual Studio.  
  
2.  Otwórz do edycji plik Program.vb lub plik Program.cs i Dodaj następujący kod.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Ograniczanie wiersza zaufania ClickOnce  
 Ograniczenie wiersza zaufania. Dzięki temu rozwiązań muszą być podpisane przy mają znane tożsamości, zanim użytkownicy są monitowani o decyzji dotyczącej zaufania certyfikatom Authenticode.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby ograniczyć wiersza zaufania ClickOnce za pomocą Edytora rejestru  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz `regedit`, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli są one jeszcze nie istnieją, z powiązanymi wartościami, które przedstawiono w poniższej tabeli.  
  
    |Podklucz wartość ciągu|Wartość|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Aby ograniczyć programowo wiersza zaufania ClickOnce  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C# w programie Visual Studio.  
  
2.  Otwórz do edycji plik Program.vb lub plik Program.cs i Dodaj następujący kod.  
  
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
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Wyłączenie wiersza zaufania ClickOnce  
 Wiersz zaufania można wyłączyć, aby użytkownicy końcowi nie podano opcję, aby zainstalować rozwiązania, które nie są już zaufane w swoich zasad zabezpieczeń.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby wyłączyć wiersz zaufania ClickOnce za pomocą Edytora rejestru  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz `regedit`, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli są one jeszcze nie istnieją, z powiązanymi wartościami, które przedstawiono w poniższej tabeli.  
  
    |Podklucz wartość ciągu|Wartość|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Aby wyłączyć programowo wiersza zaufania ClickOnce  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C# w programie Visual Studio.  
  
2.  Otwórz do edycji plik Program.vb lub plik Program.cs i Dodaj następujący kod.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Porady: włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Instrukcje: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)