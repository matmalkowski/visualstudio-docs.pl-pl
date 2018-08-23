---
title: Kodowania i linie podziału | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fd03dba0dfb13723fcb44d489a7b850aebeb1e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679638"
---
# <a name="encodings-and-line-breaks"></a>Kodowania i linie podziału
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [kodowania i podziały wierszy](https://docs.microsoft.com/visualstudio/ide/encodings-and-line-breaks).  
  
W programie Visual Studio można używać **pliku/zaawansowane opcje zapisywania** ma ustawienia, aby określić typ podział wiersza znakami możesz. Można również zmienić kodowanie pliku przy użyciu tych samych ustawień.  
  
> [!NOTE]
>  W przypadku niektórych typów ustawień środowiska deweloperskiego (Visual Basic, F #, sieci Web Development) mogą nie być widoczne **zaawansowane opcje zapisywania** w menu. Aby zmienić swoje ustawienia (na przykład aby ogólne), otwórz **narzędzia / Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 W programie Visual Studio, następujące znaki są interpretowane jako podziały wierszy:  
  
-   CRLF: Znaku powrotu karetki i wysuwu wiersza znaki Unicode 000 D + 000A  
  
-   LF: Znak nowego wiersza, Unicode 000A  
  
-   Ustaw: Następny wiersz znaków Unicode 0085  
  
-   LS: Separator wiersza, znaków Unicode 2028  
  
-   PS: Separator akapitu, znaków Unicode 2029  
  
 Tekst, który jest kopiowany z innych aplikacji zachowuje oryginalne kodowanie i znaki podziału wiersza. Na przykład po Kopiuj tekst ze Schowka i wklej go do pliku tekstowego w programie Visual Studio tekst ma tych samych ustawień, których go w Notatniku.  
  
 Po otwarciu pliku, który zawiera znaki podziału wiersza w innej, zobaczysz okno dialogowe z pytaniem, czy znaki podziału wiersza niespójne powinny być znormalizowane i jakiego typu podziałów wiersza, aby wybrać.



