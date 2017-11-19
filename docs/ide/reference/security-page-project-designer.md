---
title: "Strona zabezpieczeń, Projektant projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4eaa6a746f67c891e9e4979f9c5b06202383e5f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="security-page-project-designer"></a>Strona zabezpieczeń, Projektant projektu
**Zabezpieczeń** strony **projektanta projektu** służy do konfigurowania ustawień zabezpieczeń dostępu kodu dla aplikacji, które są wdrażane za pomocą [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Aby uzyskać dostęp do **zabezpieczeń** kliknij węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** zostanie wyświetlony, kliknij przycisk **zabezpieczeń** kartę.  
  
## <a name="security-settings"></a>Ustawienia zabezpieczeń  
 **Włączanie ustawień zabezpieczeń technologii ClickOnce**  
 Określa, czy ustawienia zabezpieczeń zostały włączone w czasie projektowania. Po wyłączeniu tej opcji, wszystkie pozostałe opcje na **zabezpieczeń** strony są niedostępne.  
  
> [!NOTE]
>  Po opublikowaniu aplikacji za pomocą **publikowania** kreatora, ta opcja jest automatycznie włączone.  
  
 Po wybraniu tej opcji, masz wybór wybierając jedną z dwóch przycisków radiowych: **to jest aplikacja pełne zaufanie** lub **jest częściowo zaufanych aplikacji**.  
  
 Domyślnie w przypadku projektów aplikacji przeglądarki sieci Web WPF ta opcja jest zaznaczona.  
  
 Domyślnie dla wszystkich innych typów projektów ta opcja jest zaznaczona.  
  
 **To jest aplikacja pełnego zaufania**  
 Jeśli wybierzesz tę opcję, aplikacji żądania uprawnień pełnego zaufania, jeśli jest zainstalowana lub uruchomić na komputerze klienckim. Unikaj przy użyciu pełnego zaufania, jeśli to możliwe, ponieważ aplikacja zostanie przyznany nieograniczony dostęp do zasobów, takich jak system plików i rejestru.  
  
 Domyślnie w przypadku projektów aplikacji przeglądarki sieci Web WPF ta opcja ma ustawioną zaufania częściowego.  
  
 Domyślnie dla wszystkich innych typów projektów opcja jest ustawiona na pełne zaufanie.  
  
 **To jest częściowo zaufanych aplikacji**  
 Jeśli wybierzesz tę opcję, aplikacji żądań uprawnieniami częściowego zaufania, jeśli jest zainstalowana lub uruchomić na komputerze klienckim. *Częściowa relacja zaufania* oznacza, że tylko akcje, które są dozwolone w obszarze uprawnienia zabezpieczeń dostępu kodu żądany zostanie uruchomiony. Aby uzyskać więcej informacji na temat konfigurowania uprawnień zabezpieczeń, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Można określić ustawienia zabezpieczeń częściowego zaufania, konfigurując opcje w **uprawnień zabezpieczeń ClickOnce** obszaru.  
  
## <a name="clickonce-security-permissions"></a>Uprawnienia zabezpieczeń technologii ClickOnce  
 **Strefy, aplikacja zostanie zainstalowana z**  
 Określa domyślny zestaw uprawnień zabezpieczeń dostępu kodu. Wybierz **Internet** lub **lokalny Intranet** ograniczonych uprawnień ustawić, lub opcję **(niestandardowy)** w celu skonfigurowania uprawnień niestandardowych ustawić. Jeśli aplikacja wymaga więcej uprawnień niż przyznane w strefie, monit zaufania ClickOnce zostanie wyświetlony dla użytkownika końcowego można udzielać dodatkowych uprawnień. Aby uzyskać więcej informacji na temat konfigurowania uprawnień zabezpieczeń, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Domyślnie projektów aplikacji przeglądarki sieci Web WPF, ta opcja jest ustawiona na **Internet**.  
  
 **Edytuj uprawnienia XML**  
 Otwiera szablon manifestu aplikacji (app.manifest) do konfigurowania uprawnień dla **(niestandardowy)** zestaw uprawnień.  
  
 **Zaawansowane**  
 Otwiera [okno dialogowe Zaawansowane ustawienia zabezpieczeń](../../ide/reference/advanced-security-settings-dialog-box.md), który służy do konfigurowania ustawień do debugowania aplikacji z ograniczonymi uprawnieniami. Ustawienia te są sprawdzane podczas debugowania i wyjątków uprawnienia wskazują, że aplikacja może wymagać więcej uprawnień niż zdefiniowana w strefie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)   
 [Porady: włączanie ustawień zabezpieczeń technologii ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Zabezpieczenia ClickOnce i wdrażania](../../deployment/clickonce-security-and-deployment.md)   
 [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)   
 [Okno dialogowe Ustawienia zaawansowane zabezpieczenia](../../ide/reference/advanced-security-settings-dialog-box.md)