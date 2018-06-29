---
title: Zaawansowane ustawienia zabezpieczeń — Okno dialogowe
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: 3910383733171775bd1f25e230cbb896648034bb
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089545"
---
# <a name="advanced-security-settings-dialog-box"></a>Zaawansowane ustawienia zabezpieczeń — Okno dialogowe

To okno dialogowe służy do określenia ustawień zabezpieczeń dotyczące debugowania w strefie.

![Zaawansowane okno dialogowe Ustawienia zabezpieczeń w programie Visual Studio](../media/advanced-security-settings.png)

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** zostanie wyświetlony, kliknij przycisk **zabezpieczeń** kartę. Na **zabezpieczeń** wybierz pozycję **włączenia ustawień zabezpieczeń technologii ClickOnce**, kliknij przycisk **jest częściowo zaufanych aplikacji**, a następnie kliknij przycisk **zaawansowane**.

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

**Przyznać aplikacji dostęp do witryny pochodzenia**

Jeśli zaznaczysz to pole wyboru, aplikacji można uzyskać dostępu do witryny sieci Web lub udział serwera, na którym jest opublikowana. Domyślnie ta opcja jest zaznaczona.

**Debuguj aplikację tak, jakby była pobrana z następującego adresu URL**

Jeśli trzeba umożliwić aplikacji dostęp do witryny sieci Web lub udział serwera odpowiadającego **URL instalacji** określone na **publikowania** Wprowadź tutaj tego adresu URL. Ta opcja jest dostępna tylko wtedy, gdy **udzielić dostępu aplikacji do witryny pochodzenia** jest zaznaczone.

## <a name="see-also"></a>Zobacz także

- [Strona zabezpieczeń, Projektant projektu](../../ide/reference/security-page-project-designer.md)