---
title: "Praca z tekstury i obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7c15d6bd2bd50b8ba8c5075ab2d90287e3a4750
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-textures-and-images"></a>Praca z obrazami i teksturami
Za pomocą edytora obrazów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do tworzenia i modyfikowania tekstury i obrazów. Edytor obrazów obsługuje sformatowanego formatów obrazów i tekstury, takich jak te, które są używane do rozwoju aplikacji DirectX.  
  
> [!NOTE]
>  Edytor obrazów nie obsługuje niski color obrazów, takich jak ikony i kursory. Aby utworzyć lub zmodyfikować te rodzaje obrazów, użyj [edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).  
  
## <a name="textures-and-images"></a>Tekstury i obrazów  
 Tekstury i obrazy są na poziomie podstawowym, tylko tabele danych, które służą do zapewniania visual szczegółów w aplikacjach grafiki. Rodzaj szczegółowości, który zawiera obraz lub tekstury zależy od tego, jak jest używany, ale kolorów, wartości alfa (przezroczystości) powierzchni normalne i wysokość wartości są typowe przykłady. Główną różnicą między tekstury i obrazu jest tekstury jest ma można używać razem z reprezentacji kształtu — zwykle model 3-w — Express cały obiekt lub sceny, ale obraz jest zazwyczaj autonomiczna reprezentację sceny lub obiektu .  
  
 Typowych rodzajów tekstury obejmują:  
  
 Mapy tekstury  
 Mapy tekstury zawiera wartości koloru są organizowane jako jedno-, dwu- lub trójwymiarowy macierzy. Są one używane, aby udostępnić szczegóły koloru na odpowiednim obiekcie. Kolory często są zakodowane za pomocą kanałów kolorów RGB (czerwony, zielony, niebieski) i może zawierać czwarty kanał alfa, reprezentujący przezroczystość. Rzadziej, kolory może być kodowane w inny schemat kolorów lub czwarty kanał może zawierać danych innych niż alfa — na przykład wysokość.  
  
 Mapy normalne  
 Mapy normalne zawierają wektorów powierzchni. Są one używane do świadczenia oświetlenia szczegóły w odpowiednich obiektów. Normalne często są zakodowane przy użyciu składników kolor czerwony, zielonemu i niebieskiemu do przechowywania x, y i wymiarów z wektora. Jednak istnieje inne kodowanie — na przykład kodowanie, które są oparte na Współrzędne biegunowe.  
  
 Wysokość mapy  
 Wysokość mapy zawiera dane wysokości pola. Są one używane do zapewnienia formę szczegółów geometrycznych na odpowiednim obiekcie — przy użyciu programu do cieniowania kodu do obliczenia pożądanych efektów — lub w celu zapewnienia do celów, takich jak Generowanie terenu punktów danych. Wysokość wartości najczęściej są zakodowane za pomocą jednego kanału tekstury.  
  
 Mapuje modułu  
 Mapy modułu mogą zawierać różne typy danych — na przykład kolorów lub wektorów — ale dzielą się na sześciu tekstury na powierzchni modułu. W związku z tym modułu mapy nie są próbkowane podając współrzędnych tekstury, ale podając wektora którego pochodzi Centrum modułu; próbki w momencie, gdy wektora przecina modułu. Mapy modułu służą do zapewniania zbliżenia środowiska, który może służyć do obliczenia odbić — jest to nazywane *mapowania środowiska*— lub w celu zapewnienia teksturę dla kulistego obiektów z mniejszymi zniekształceniami niż podstawowy, zapewniają dwuwymiarowa tekstury.  
  
 Wszelkie tekstury może być zakodowane i skompresowane na wiele sposobów, będące prostopadłym do typu danych przechowujący teksturę, albo wymiary lub "kształtu" tekstury. Jednak inne kodowanie i metody kompresji yield lepsze wyniki dla różnych typów danych.  
  
 Edytor obrazów służy do tworzenia i modyfikowania obrazów w sposób przypominający inne edytory obrazów i tekstury. Edytor obrazów również zapewnia mipmapowaniem i inne funkcje do użytku z 3-grafiki i obsługuje wiele formatów wysokiej skompresowany, przyspieszane sprzętowo tekstury, które obsługuje DirectX.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Edytor obrazów](../designers/image-editor.md)|Opisuje sposób pracy z tekstury i obrazów za pomocą edytora obrazów.|  
|[Przykłady Edytora obrazów](../designers/image-editor-examples.md)|Zawiera łącza do tematów, które przedstawiają sposób wykonywania typowych zadań obrazu za pomocą edytora obrazów.|