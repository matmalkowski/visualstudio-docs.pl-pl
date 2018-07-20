---
title: 'Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c30766b50692052ec9fdd04c5ec1b156738c47b5
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152974"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami
Deweloperzy najprawdopodobniej używasz komputer deweloperski przy użyciu uprawnień pełnego zaufania, dzięki czemu nie będą widzieć same wyjątki zabezpieczeń podczas debugowania aplikacji ClickOnce, które użytkownik końcowy może zostać wyświetlony po uruchomieniu z ograniczonymi uprawnieniami.  
  
 Aby przechwytywać te wyjątki, konieczne będzie można debugować aplikację za pomocą tych samych uprawnień jako użytkownik końcowy. Debugowanie przy użyciu ograniczonych uprawnień można włączyć dla **zabezpieczeń** strony **projektanta projektu**.  
  
 Ponadto podczas tworzenia aplikacji, które wywołują usługi sieci Web, te usługi sieci Web często znajdują się na komputerze deweloperskim. Po wdrożeniu, użytkownik końcowy będzie dostęp do tych usług sieci Web z innego adresu URL. Aby emulować doświadczenia użytkownika końcowego podczas debugowania, można określić, że adres URL i debuger traktują usług sieci Web tak, jakby były one wywoływane z tego adresu URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Aby włączyć debugowanie z ograniczonymi uprawnieniami  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  W **projektanta projektu**, kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **Włącz ustawienie zabezpieczeń ClickOnce** pole wyboru, a następnie kliknij przycisk **to częściowo zaufanych aplikacji** przycisku opcji.  
  
4.  Kliknij przycisk **zaawansowane** przycisku.  
  
5.  Wybierz **Debuguj aplikację z wybranym zestawem uprawnień** pole wyboru, a następnie kliknij przycisk **OK**.  
  
     Podczas debugowania aplikacji, wszelkie próby uprawnienie, które nie jest częścią zestawu uprawnień dostępu zgłosi wyjątek zabezpieczeń.  
  
### <a name="to-specify-a-url-for-debugging"></a>Aby określić adres URL do debugowania  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  W **projektanta projektu**, kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **Włącz ustawienie zabezpieczeń ClickOnce** pole wyboru, a następnie kliknij przycisk **to częściowo zaufanych aplikacji** przycisku opcji.  
  
4.  Kliknij przycisk **zaawansowane** przycisku.  
  
5.  Wybierz **Debuguj aplikację z wybranym zestawem uprawnień** pole wyboru, a następnie kliknij przycisk **OK**.  
  
6.  W **Debuguj aplikację tak, jakby zostały pobrane z następującego adresu URL** polu tekstowym wprowadź adres URL lub ścieżka sieciowa.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)