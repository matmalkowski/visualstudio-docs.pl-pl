---
title: ClickOnce i podpis Authenticode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7fb428cf2bffd5ae10bb9e3cce95ba4021007ef1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
*Authenticode* to technologia firmy Microsoft, która używa branżowego standardu kryptografii do podpisania kodu aplikacji przy użyciu certyfikatów cyfrowych, które zweryfikowania autentyczności wydawcy aplikacji. Za pomocą kodu Authenticode dla wdrożenia aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zmniejsza ryzyko konia trojańskiego. Koń trojański to wirusów lub innych szkodliwych program, który złośliwego innej posiadałaby jako program uzasadnionych ustanowione, zaufanego źródła. Podpisywanie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń za pomocą certyfikatu cyfrowego jest opcjonalny krok, aby sprawdzić nie zmodyfikowane pliki i zestawy.  
  
 Poniższe sekcje opisują różne typy certyfikatów cyfrowych używanych w Authenticode, jak certyfikaty są weryfikowane przy użyciu certyfikatów urzędów certyfikacji, rola stosowania sygnatur czasowych w certyfikatach i metody dla miejsca do magazynowania certyfikaty.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywania kodu  
 A *certyfikatu cyfrowego* plik, który zawiera publicznego i prywatnego klucza kryptograficznego, wraz z metadane opisujące wydawcy do której certyfikat został wystawiony i agencji, który wystawił certyfikat.  
  
 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany dla różnych typów podpisywania. Dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, musi mieć certyfikat jest prawidłowy do podpisywania kodu Authenticode. Jeśli spróbujesz zarejestrować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu innego typu certyfikatu, takie jak certyfikat cyfrowy poczty e-mail, będzie on działał. Aby uzyskać więcej informacji, zobacz [wprowadzenie do podpisywania kodu](http://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Można uzyskać certyfikat podpisywania w jeden z trzech sposobów kodu:  
  
-   Kupić ją od dostawcy certyfikatu.  
  
-   Wyświetlony jeden z grupy w organizacji odpowiedzialną za tworzenie certyfikatów cyfrowych.  
  
-   Generowanie własnego certyfikatu za pomocą polecenia cmdlet New-SelfSignedCertificate programu PowerShell lub przy użyciu MakeCert.exe, która jest dostarczana z [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak przy użyciu urzędów certyfikacji ułatwia użytkownikom  
 Certyfikat, który został wygenerowany za pomocą nowego SelfSignedCertificate lub narzędzia MakeCert.exe jest popularnie określany *samoobsługowego cert* lub *certyfikatu testowego*. Tego rodzaju certyfikatu działa podobnie jak w pliku .snk — programu .NET Framework. Składa się wyłącznie z publicznego i prywatnego klucza kryptograficznego, a nie zawiera możliwe do zweryfikowania informacji o wydawcy. Certyfikaty samoobsługowego można użyć do wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje z wysokim poziomem zaufania w intranecie. Jednak gdy te aplikacje uruchomione na komputerze klienckim [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zidentyfikować je jako pochodzący od nieznanego wydawcy. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podpisane przez certyfikaty samoobsługowego i wdrożone za pośrednictwem Internetu nie może korzystać z zaufanego wdrożenia aplikacji.  
  
 Z kolei jeśli zostanie wyświetlony certyfikat od urzędu certyfikacji, takiego jak dostawcy certyfikatu, lub dział w przedsiębiorstwie, certyfikatu zapewnia lepszą ochronę dla użytkowników. Nie tylko identyfikuje wydawcę oprogramowania podpisany, ale sprawdzi tej tożsamości, sprawdzając z urzędem certyfikacji, który podpisał go. Jeśli urząd certyfikacji nie ma głównego urzędu certyfikacji, Authenticode będzie również "łańcucha" powrotem do głównego urzędu, aby sprawdzić, czy urząd certyfikacji jest autoryzowany do wystawiania certyfikatów. Ze względów bezpieczeństwa należy używać certyfikatu wystawionego przez urząd certyfikacji, jeśli to możliwe.  
  
 Aby uzyskać więcej informacji na temat generowania samoobsługowego certyfikaty, zobacz [SelfSignedCertificate nowy](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) lub [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
### <a name="timestamps"></a>Znaczniki czasu  
 Certyfikaty używane do podpisywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji wygasają po określonego czasu, zwykle dwanaście miesięcy. Aby wyeliminować konieczność stale ponowne podpisanie aplikacji za pomocą nowego świadectwa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] obsługuje sygnatury czasowej. Gdy aplikacja jest podpisana z sygnaturą czasową, jego certyfikat będzie akceptowany nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest nieprawidłowa. Dzięki temu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą wygasłe certyfikaty, ale prawidłowe sygnatury czasowe, aby pobierać i uruchamiać. Umożliwia także zainstalowanych aplikacji z wygasłe certyfikaty kontynuować pobrać i zainstalować aktualizacje.  
  
 Aby dołączyć sygnaturę czasową serwera aplikacji, musi być dostępny serwer znaczników czasu. Aby dowiedzieć się, jak wybrać serwer znaczników czasu, zobacz [porady: logowania aplikacji i manifestów wdrożenia](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aktualizowanie wygasłych certyfikatów  
 We wcześniejszych wersjach programu .NET Framework aktualizowanie aplikacji wygaśnięciu certyfikatu, którego może spowodować aplikację przestanie działać. Aby rozwiązać ten problem, użyj jednej z następujących metod:  
  
-   Aktualizacja programu .NET Framework do w wersji 2.0 z dodatkiem SP1 lub nowszego systemu Windows XP lub w wersji 3.5 lub nowszego systemu Windows Vista.  
  
-   Odinstalowanie aplikacji, i ponowne zainstalowanie nowej wersji przy użyciu prawidłowego certyfikatu.  
  
-   Tworzenie zestawu wiersza polecenia, które aktualizuje certyfikat. Szczegółowe informacje o tym procesie można znaleźć w folderze [925521 artykuł pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Przechowywanie certyfikatów  
  
-   Certyfikaty można zapisać jako plik pfx w systemie plików, lub można je przechowywać wewnątrz kontenera kluczy. Użytkownika w domenie systemu Windows może mieć wiele kontenerów kluczy. Domyślnie program MakeCert.exe będzie certyfikaty są przechowywane w osobistych kontenera kluczy, chyba że zostanie określony, aby go należy zapisywać do pliku PFX zamiast tego. Mage.exe i MageUI.exe, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] narzędzia do tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń umożliwiają korzystanie z certyfikatów przechowywanych w każdej sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)