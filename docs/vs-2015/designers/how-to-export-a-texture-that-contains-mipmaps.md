---
title: 'Instrukcje: eksportowanie tekstury zawierającej mipmapy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a876676eed593bfa06c3e89521522d9901c58ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680735"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Porady: eksportowanie tekstury zawierającej mipmapy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: eksportowanie tekstury tego mipmapy zawiera](https://docs.microsoft.com/visualstudio/designers/how-to-export-a-texture-that-contains-mipmaps).  
  
Potok zawartości obrazu może generować mipmapy z obrazu źródłowego w ramach fazy kompilacji projektu. Jeśli nie trzeba ręcznie określać zawartości obrazu każdego poziomu MIP — co możesz zrobić, aby uzyskać pewne efekty — Generowanie mipmap w czasie kompilacji zapewnia, że zawartość mipmappingu nigdy nie stanie się poza synchronizacji i eliminuje koszty wydajności wytwarzania mipmap w czasie wykonywania.  
  
 Ten dokument przedstawia te działania:  
  
-   Konfigurowanie obrazu źródłowego, który ma być przetwarzana przez potok zawartości obrazu.  
  
-   Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap.  
  
## <a name="exporting-mipmaps"></a>Eksportowanie Mipmap  
 Mipmapping zapewnia automatyczne ekranowego poziom szczegółów wypełniający dla teksturowanych powierzchni w grze lub aplikacji 3D. Zwiększa wydajność renderowania gry lub aplikacji poprzez wstępnie obliczenie wersji tekstury, aby cała Tekstura nie musi być próbkowana w dół każdorazowo, gdy jest próbkowana.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę, która ma mipmapy  
  
1.  Rozpocznij od podstawowej tekstury. Załaduj istniejący pliku obrazu lub utwórz je, zgodnie z opisem w [porady: tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmapy, określ teksturę, która ma szerokość i wysokość, które są tego samego przekazu dwa, na przykład 64 x 64, 256 x 256 lub 512 x 512.  
  
2.  Skonfigurować pliku tekstury, który został utworzony, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla utworzonego właśnie pliku tekstury, a następnie wybierz **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potok zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **Wyłącz z kompilacji** ustawiono **nie**, a następnie wybierz  **Zastosuj** przycisku. **Potok zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.  
  
3.  Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap. Na **właściwości konfiguracji**, **potok zawartości obrazu**, **ogólne** ustaw **Generuj Mips** właściwość **Tak (/ generatemips)**.  
  
4.  Wybierz **OK** przycisku.  
  
 Podczas budowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, włącznie z poziomami MIP, a wynik jest kopiowany do katalogu wyjściowego projektu.



