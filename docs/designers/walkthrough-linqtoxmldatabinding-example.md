---
title: 'Wskazówki: Przykład LinqToXmlDataBinding'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aa99324969f7fedfea7596dce55f9167ad6bb9a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917166"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Wskazówki: Przykład LinqToXmlDataBinding
W tym przewodniku opisano przykład LinqToXmlDataBinding oraz omówiono bardziej interesującego zawartości jego dwa pliki podstawowym źródłem L2DBForm.xaml i L2DBForm.xaml.cs.

## <a name="prerequisites"></a>Wymagania wstępne
 Przed przeczytaniem tego przewodnika, zdecydowanie zalecane jest tworzenie i uruchom LinqToXmlDataBinding program zgodnie z opisem w [porady: tworzenie i uruchamianie przykład LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Uwagi
 LinqToXmlDataBinding program jest aplikacją Windows Presentation Foundation (WPF), która składa się C# i pliki źródłowe języka XAML. Zawiera osadzony dokumentu XML, który definiuje listę książek i umożliwia użytkownikowi wyświetlać, dodawać, usuwać i edytować te wpisy. Składa się z następujących dwóch plików podstawowego źródła:

-   L2DBForm.XAML zawiera kod XAML deklaracji interfejsu użytkownika (UI) głównego okna. Zawiera także definiujący dostawcy danych i osadzone dokumentu XML list książki sekcji zasobów okna.

-   L2DBForm.XAML.cs zawiera inicjowanie i metod obsługi zdarzeń skojarzonych z interfejsu użytkownika.

 Okno główne podzielono na następujące cztery pionowy części interfejsu użytkownika:

-   **XML** Wyświetla pierwotne źródło XML listy książki osadzonych.

-   **Skoroszyt listy** wpisy książki będzie wyświetlany jako tekst standardowy i umożliwia użytkownikowi wybierz i Usuń poszczególne pozycje.

-   **Edytuj wybraną książkę** umożliwia użytkownikowi edytowanie wartości skojarzone z wpisu książki obecnie wybrany.

-   **Dodawanie nowej książki** umożliwia tworzenie nowy wpis książki na podstawie wartości wprowadzonej przez użytkownika.

## <a name="in-this-section"></a>W tej sekcji

|Temat|Opis|
|-----------|-----------------|
|[Kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Zawiera opis kodu XAML w pliku L2DBForm.xaml i zawartość.|
|[Kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Zawiera opis kodu źródłowego C# w pliku L2DBForm.xaml.cs i zawartość.|

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML — przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Instrukcje: kompilowanie i uruchamianie elementu LinqToXmlDataBinding — przykład](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)