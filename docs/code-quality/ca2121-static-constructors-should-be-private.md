---
title: 'CA2121: Konstruktory statyczne powinny być prywatne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6eef1097565090fd1b9be572f9a33afed9afed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Konstruktory statyczne powinny być prywatne
|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ ma konstruktora statycznego, który nie jest prywatny.

## <a name="rule-description"></a>Opis reguły
 Konstruktor statyczny, znanej także jako konstruktora klasy, służy do inicjowania typu. System wywołuje statyczny konstruktor przed utworzeniem pierwszego wystąpienia typu lub przed odwołaniem do któregokolwiek ze statycznych elementów członkowskich. Użytkownik nie ma kontroli nad podczas wywołania konstruktora statycznego. Jeśli konstruktor statyczny nie jest prywatny, może być wywołany przez kod inny niż system. W zależności od operacji, które są wykonywane w konstruktorze, może to spowodować nieoczekiwane zachowanie.

 Ta reguła jest wymuszone przez Kompilatory języka C# i Visual Basic.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Naruszenia są zazwyczaj spowodowane jedną z następujących czynności:

-   Definicja Konstruktor statyczny dla danego typu i nie wprowadzono go prywatnych.

-   Kompilator języka programowania dodany statycznego konstruktora domyślnego do typu i nie wprowadzono go prywatnych.

 Aby rozwiązać pierwszego rodzaju naruszenia, upewnij Twojej statycznego konstruktora prywatnego. Aby naprawić drugiego rodzaju, Dodaj Konstruktor prywatny statyczny do typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj naruszenia. Jeśli projekt oprogramowania wymaga jawnego wywołania konstruktora statycznego, jest prawdopodobne, że projekt zawiera poważne wady i należy ją sprawdzić.