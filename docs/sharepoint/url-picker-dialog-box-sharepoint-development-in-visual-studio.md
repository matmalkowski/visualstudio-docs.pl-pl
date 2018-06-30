---
title: Okno dialogowe selektora URL (Programowanie SharePoint w Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7820723c88fd76639fa47e5c97ad179a208fc18
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120289"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Okno dialogowe selektora URL (Programowanie SharePoint w Visual Studio)
  W okno dialogowe selektora URL można wybrać pliki takie jak pliki strony wzorcowej lub pliki obrazów, które znajdują się w projekcie lub na lokalnym serwerze z programem SharePoint.  
  
 To okno dialogowe jest wyświetlany, gdy masz opcję, aby wybrać plik do ustawienia właściwości. To okno dialogowe można otworzyć, wybierając przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) obok różne właściwości w **właściwości** okna. Przycisk wielokropka jest także wyświetlany jako IntelliSense Monituj podczas przypisywania wartości do określonych atrybutów w **źródła** Widok projektanta.  
  
## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika
 **Foldery projektu**  
 Wyświetlanie listy folderów zdefiniowanych w projekcie, lub na lokalnym serwerze z programem SharePoint. Wybierz przycisk rozszerzenia, aby wyświetlić podfoldery.  
  
 Rozwiń węzeł **projektu** węzeł, aby wybrać pliki w projekcie. Aby w oknie dialogowym są wyświetlane jako możliwy, pliki w projekcie musi spełniać następujące kryteria:  
  
-   Plik musi być zawarte w zamapowany folder.  
  
-   Plik musi być dodany do pakietu rozwiązania.  
  
-   Nie można zlokalizować pliku w innym projekcie.  
  
 Do plików, które nie spełniają te kryteria, należy ręcznie wprowadzić ścieżkę pliku.  
  
 Rozwiń węzeł **serwera** węzeł, aby wybrać pliki, które znajdują się na lokalnym serwerze z programem SharePoint. Aby w oknie dialogowym są wyświetlane jako możliwy, te pliki muszą spełniać następujące kryteria:  
  
-   Plik musi znajdować się w jednym z następujących folderów mapowanych: **obrazów**, **układów**, lub **ControlTemplates**.  
  
-   Nie można zlokalizować pliku w bazie danych zawartości programu SharePoint.  
  
 Do plików, które nie spełniają te kryteria, należy ręcznie wprowadzić ścieżkę pliku.  
  
 **Zawartość folderu**  
 Wyświetla listę plików w wybranym folderze. Wybierz plik, a następnie wybierz pozycję **OK** przycisk, aby zamknąć okno dialogowe i Wyślij zaznaczenie do procesu, który ją.  
  
 **Pliki typu**  
 Można wybrać z listy plików, które są odpowiednie do zadania, które są wykonywane.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Tworzenie składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
