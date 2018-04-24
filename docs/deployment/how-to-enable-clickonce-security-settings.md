---
title: 'Porady: włączanie ustawień zabezpieczeń technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc3f87e590c6b915d5b3d9db5d2517d80965dd6c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-enable-clickonce-security-settings"></a>Porady: włączenie ustawień zabezpieczeń technologii ClickOnce
Zabezpieczenia dostępu kodu dla aplikacji ClickOnce musi być włączona, aby opublikować aplikację. Odbywa się to automatycznie podczas publikowania aplikacji przy użyciu Kreatora publikowania.  
  
 W niektórych przypadkach włączenie zabezpieczeń dostępu kodu może wpłynąć na wydajność podczas kompilowania lub debugowania aplikacji; w takich przypadkach możesz tymczasowo wyłączyć ustawienia zabezpieczeń.  
  
 Ustawienia zabezpieczeń ClickOnce można włączać lub wyłączać dla **zabezpieczeń** strony **projektanta projektu**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Aby włączyć ustawień zabezpieczeń technologii ClickOnce  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
     Teraz można dostosować ustawienia zabezpieczeń dla aplikacji na stronie zabezpieczenia.  
  
    > [!NOTE]
    >  To pole wyboru jest automatycznie wybierany zawsze aplikacji jest publikowany razem **publikowania** kreatora.  
  
### <a name="to-disable-clickonce-security-settings"></a>Aby wyłączyć ustawień zabezpieczeń technologii ClickOnce  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wyczyść **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
     Aplikacja jest uruchamiana przy użyciu ustawień zabezpieczeń Pełne zaufanie; wszystkie ustawienia na **zabezpieczeń** strony zostaną zignorowane.  
  
    > [!NOTE]
    >  Zawsze, gdy aplikacja jest opublikowana przy użyciu Kreatora publikowania tego pola wyboru zostanie wybrany; należy go wyczyścić ponownie po każdej publikacji powiodło się.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
