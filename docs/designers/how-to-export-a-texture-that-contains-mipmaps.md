---
title: 'Porady: eksportowanie tekstury zawierającej mipmapy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae3b12ffa91b419717e91125b658f29e7d74deb6
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2018
ms.locfileid: "37923897"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Instrukcje: eksportowanie tekstury zawierającej mipmapy

Potok zawartości obrazu może generować mipmapy z obrazu źródłowego w ramach fazy kompilacji projektu. Aby uzyskać pewne efekty, czasami trzeba ręcznie określać zawartości obrazu każdego poziomu MIP. Gdy nie trzeba ręcznie określać zawartości obrazu każdego poziomu MIP, generowanie mipmap w czasie kompilacji zapewnia, że zawartość mipmappingu nigdy nie stanie się poza synchronizacji. Eliminuje koszty wydajności wytwarzania mipmap w czasie wykonywania.

W tym artykule omówiono:

- Konfigurowanie obrazu źródłowego, który ma być przetwarzana przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap.

## <a name="export-mipmaps"></a>Eksportowanie mipmap

Mipmapping zapewnia automatyczne ekranowego poziom szczegółów wypełniający dla teksturowanych powierzchni w grze lub aplikacji 3D. Zwiększa wydajność renderowania gry lub aplikacji poprzez wstępnie obliczenie wersji tekstury. Wstępne przetwarzanie próbkowana w dół wersjami oznacza, że cały Tekstura nie musiała być próbkowana w dół każdorazowo go próbkowania.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę, która ma mipmapy

1.  Rozpocznij od podstawowej tekstury. Załaduj istniejący pliku obrazu lub utwórz je, zgodnie z opisem w [porady: tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmapy, określ teksturę, która ma szerokość i wysokość, które są tego samego przekazu dwa, na przykład 64 x 64, 256 x 256 lub 512 x 512.

2.  Skonfigurować pliku tekstury, który został utworzony, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku tekstury, został utworzony, a następnie wybierz **właściwości**. Na **właściwości konfiguracji** > **ogólne** ustaw **typu elementu** właściwości **potok zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **Wyłącz z kompilacji** ustawiono **nie**. Wybierz **zastosować**.

   **Potok zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.

3.  Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap. Na **właściwości konfiguracji** > **potok zawartości obrazu** > **ogólne** ustaw **Generuj Mips** właściwości **tak (/ generatemips)**.

4.  Wybierz **OK**.

Podczas budowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, włącznie z poziomami MIP. Wynik jest kopiowany do katalogu wyjściowego projektu.