---
title: Zaawansowane ustawienia zabezpieczeń — okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1dad7843d42aeaf0c2871f8b76c840a12cd4186
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-security-settings-dialog-box"></a>Zaawansowane ustawienia zabezpieczeń — Okno dialogowe
To okno dialogowe służy do określenia ustawień zabezpieczeń dotyczące debugowania w strefie.  
  
 Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** zostanie wyświetlony, kliknij przycisk **zabezpieczeń** kartę. Na **zabezpieczeń** wybierz pozycję **włączenia ustawień zabezpieczeń technologii ClickOnce**, kliknij przycisk **jest częściowo zaufanych aplikacji**, a następnie kliknij przycisk **zaawansowane**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Debuguj aplikację z wybranym zestawem uprawnień**  
 Jeśli to pole wyboru jest zaznaczone, zestaw uprawnień wybranego na **zabezpieczeń** strona jest używana podczas debugowania. Domyślnie ta opcja jest zaznaczona.  
  
 Debugowanie w strefie zabezpieczeń do pracy, ta opcja musi być włączone; Ponadto **włączyć procesu hostingu Visual Studio** opcji (dostępne na **debugowania** strony **projektanta projektu**) musi być włączona.  
  
 W przypadku projektów aplikacji przeglądarki sieci Web WPF **Debuguj aplikację z wybranym zestawem uprawnień** opcji jest zaznaczony i wyłączone.  
  
 **Przyznać aplikacji dostęp do witryny pochodzenia**  
 Jeśli zaznaczysz to pole wyboru, aplikacji można uzyskać dostępu do witryny sieci Web lub udział serwera, na którym jest opublikowana. Domyślnie ta opcja jest zaznaczona.  
  
 **Debuguj aplikację tak, jakby była pobrana z następującego adresu URL**  
 Jeśli trzeba umożliwić aplikacji dostęp do witryny sieci Web lub udział serwera odpowiadającego **URL instalacji** określone na **publikowania** strony, wpisz w tym miejscu tego adresu URL. Ta opcja jest dostępna tylko wtedy, gdy **udzielić dostępu aplikacji do witryny pochodzenia** jest zaznaczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona zabezpieczeń, Projektant projektu](../../ide/reference/security-page-project-designer.md)