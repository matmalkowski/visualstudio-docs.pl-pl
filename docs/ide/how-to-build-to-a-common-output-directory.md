---
title: 'Porady: kompilacja — przejście do wspólnego katalogu wyjściowego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f45890224684ff2e4c411875ab61bdfb698cfb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942048"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Porady: kompilacja — przejście do wspólnego katalogu wyjściowego

Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kompilacje każdego projektu w rozwiązaniu w osobnym folderze wewnątrz rozwiązania. Można zmienić ścieżki danych wyjściowych kompilacji projektów wymuszenie wszystkie dane wyjściowe można umieścić w tym samym folderze.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Można umieścić rozwiązanie wszystkich danych wyjściowych w katalog wspólny

1.  Kliknij jeden projekt w rozwiązaniu.

2.  Na **projektu** menu, kliknij przycisk **właściwości**.

3.  W zależności od typu projektu, kliknij opcję **skompilować** kartę lub **kompilacji** , a następnie ustaw **ścieżka wyjściowa** do folderu do użycia dla wszystkich projektów w rozwiązaniu.

4.  Powtórz kroki od 1 do 3 dla wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Porady: zmiana budowy katalogu wyjściowego](../ide/how-to-change-the-build-output-directory.md)