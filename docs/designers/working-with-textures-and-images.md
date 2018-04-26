---
title: Praca z obrazami i teksturami
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c93b77cde590209b9217666dd1ac8382dbdd4475
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="work-with-textures-and-images"></a>Praca z tekstury i obrazów

Edytor obrazów programu Visual Studio do tworzenia i modyfikowania tekstury i obrazów. Edytor obrazów obsługuje sformatowanego formatów obrazów i tekstury, takich jak te, które są używane do rozwoju aplikacji DirectX.

> [!NOTE]
> Edytor obrazów nie obsługuje niski color obrazów, takich jak ikony i kursory. Aby utworzyć lub zmodyfikować te rodzaje obrazów, użyj [edytor obrazów dla ikon (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Tekstury i obrazów

Tekstury i obrazy są na poziomie podstawowym, tylko tabele danych, które służą do zapewniania visual szczegółów w aplikacjach grafiki. Rodzaj szczegółowości, który zawiera obraz lub tekstury zależy od tego, jak jest używany, ale kolorów, wartości alfa (przezroczystości) powierzchni normalne i wysokość wartości są typowe przykłady. Główną różnicą między tekstury i obrazu jest tekstury jest ma można używać razem z reprezentacji kształtu — zwykle modelu 3D — Express cały obiekt lub sceny, ale obraz jest zazwyczaj autonomiczna reprezentację sceny lub obiektu.

Wszelkie tekstury może być zakodowane i skompresowane na wiele sposobów, będące prostopadłym do typu danych przechowujący teksturę, albo wymiary lub "kształtu" tekstury. Jednak inne kodowanie i metody kompresji yield lepsze wyniki dla różnych typów danych.

Edytor obrazów służy do tworzenia i modyfikowania obrazów w sposób przypominający inne edytory obrazów i tekstury. Edytor obrazów również zapewnia mipmapowaniem i inne funkcje do użytku z grafiki 3D i obsługuje wiele formatów wysokiej skompresowany, przyspieszane sprzętowo tekstury, które obsługuje DirectX.

Typowych rodzajów tekstury obejmują:

### <a name="texture-maps"></a>Mapy tekstury

Mapy tekstury zawiera wartości koloru są organizowane jako jedno-, dwu- lub trójwymiarowy macierzy. Są one używane, aby udostępnić szczegóły koloru na odpowiednim obiekcie. Kolory często są zakodowane za pomocą kanałów kolorów RGB (czerwony, zielony, niebieski) i może zawierać czwarty kanał alfa, reprezentujący przezroczystość. Rzadziej, kolory może być kodowane w inny schemat kolorów lub czwarty kanał może zawierać danych innych niż alfa — na przykład wysokość.

### <a name="normal-maps"></a>Mapy normalne

Mapy normalne zawierają wektorów powierzchni. Są one używane do świadczenia oświetlenia szczegóły w odpowiednich obiektów. Normalne często są zakodowane przy użyciu składników kolor czerwony, zielonemu i niebieskiemu do przechowywania x, y i wymiarów z wektora. Jednak istnieje inne kodowanie — na przykład kodowanie, które są oparte na Współrzędne biegunowe.

### <a name="height-maps"></a>Wysokość mapy

Wysokość mapy zawiera dane wysokości pola. Są one używane do zapewnienia formę szczegółów geometrycznych na odpowiednim obiekcie — przy użyciu programu do cieniowania kodu do obliczenia pożądanych efektów — lub w celu zapewnienia do celów, takich jak Generowanie terenu punktów danych. Wysokość wartości najczęściej są zakodowane za pomocą jednego kanału tekstury.

### <a name="cube-maps"></a>Mapuje modułu

Mapy modułu mogą zawierać różne typy danych — na przykład kolorów lub wektorów — ale dzielą się na sześciu tekstury na powierzchni modułu. W związku z tym modułu mapy nie są próbkowane podając współrzędnych tekstury, ale podając wektora którego pochodzi Centrum modułu; próbki w momencie, gdy wektora przecina modułu. Mapy modułu służą do zapewniania zbliżenia środowiska, który może służyć do obliczenia odbić — jest to nazywane *mapowania środowiska*— lub w celu zapewnienia teksturę dla kulistego obiektów z mniejszymi zniekształceniami niż podstawowy, zapewniają dwuwymiarowa tekstury.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje sposób pracy z tekstury i obrazów za pomocą edytora obrazów.|
|[Przykłady Edytora obrazów](../designers/image-editor-examples.md)|Zawiera łącza do tematów, które przedstawiają sposób wykonywania typowych zadań obrazu za pomocą edytora obrazów.|