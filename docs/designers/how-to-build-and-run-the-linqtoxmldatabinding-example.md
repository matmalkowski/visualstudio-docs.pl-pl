---
title: "Porady: tworzenie i uruchamianie przykład LinqToXmlDataBinding | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 57f4259e51650b9af1788195b39fc8a72becbfde
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Porady: tworzenie i uruchamianie przykład LinqToXmlDataBinding

W tym temacie przedstawiono sposób tworzenia i kompilowania projektu programu Visual Studio LinqToXmlDataBinding i uruchamiania programu przykładzie wynikowa LinqToXmlDataBinding Windows Presentation Foundation (WPF).

Aby uzyskać więcej informacji na temat programu Visual Studio, zobacz [programu Visual Studio IDE omówienie](../ide/visual-studio-ide.md).

## <a name="creating-and-populating-the-project"></a>Tworzenie i wypełnianie projektu

### <a name="to-create-the-starting-project"></a>Aby utworzyć projekt początkowy

1. Uruchom program Visual Studio i utworzyć aplikację WPF C# o nazwie LinqToXmlDataBinding. Projekt musi korzystać z programu .NET Framework 3.5 (lub nowszej).

1. Jeśli nie jest jeszcze nie istnieje, dodaj odwołania do projektu dla następujących zestawów platformy .NET:

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl + Shift + B**, uruchom go przez naciśnięcie przycisku **F5**. Projekt należy skompilować bez błędów i Uruchom jako ogólnego aplikacji WPF.

### <a name="to-add-custom-code-to-the-project"></a>Aby dodać kod niestandardowy do projektu

1. W Eksploratorze rozwiązań Zmień nazwę pliku źródłowego Window1.xaml na L2XDBForm.xaml. Plik źródłowy zależnych Window1.xaml.cs powinny zostać zmienione automatycznie do L2XDBForm.xaml.cs.

1. Zastąp kod źródłowy znaleziono w pliku L2XDBForm.xaml z sekcji kod z tematu [kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). Użyj widoku kodu XAML do pracy z tym plikiem.

1. Podobnie, Zastąp kod w źródła w L2XDBForm.xaml.cs [kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. W pliku App.xaml Zastąp wszystkie wystąpienia ciągu "Window1.xaml" z "L2XDBForm.xaml".

1. Tworzenie rozwiązania naciśnięcie **Ctrl + Shift + B**.

## <a name="running-the-program"></a>Uruchomienie programu

LinqToXmlDataBinding program umożliwia użytkownikowi wyświetlanie i manipulowanie listę książek są przechowywane jako osadzonego elementu XML.

### <a name="to-run-the-program-and-view-the-book-list"></a>Uruchom program i wyświetlania listy książek

- Uruchom LinqToXmlDataBinding naciskając **F5** (**Rozpocznij debugowanie**) lub **Ctrl + F5** (**uruchomić bez debugowania**).

   Okno programu z tytułem **za pomocą LINQ do XML powiązanie danych WPF** jest wyświetlany.

- Zwróć uwagę, w górnej części interfejsu użytkownika, który wyświetla nieprzetworzonego **XML** reprezentujący listy książek. Pojawi się przy użyciu programu WPF <xref:System.Windows.Controls.TextBlock> formantu, który nie obsługuje interakcji za pomocą klawiatury lub myszy.

- Druga sekcja pionowy, o nazwie **listy książek**, wyświetla Lista uporządkowana książek jako zwykły tekst. Używa <xref:System.Windows.Controls.ListBox> kontrolkę umożliwiającą wybór jednak za pomocą klawiatury lub myszy.

### <a name="to-add-and-delete-books-from-the-list"></a>Dodawanie i usuwanie książek z listy

- Aby usunąć istniejącą książkę z listy, wybierz go w **listy książek** sekcji, a następnie kliknij przycisk **Usuń zaznaczone książki** przycisku. Należy zauważyć, że wpis książki została usunięta z księgi i raw listy Źródło XML.

- Aby dodać nową książkę do listy, wprowadź wartości w **identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> formantów w ostatniej sekcji **Dodawanie nowej książki**, następnie kliknij przycisk **Dodaj Podręcznik** przycisku. Należy pamiętać, że książce jest dołączany do listy w książce i zawartości XML. Ten program nie można zweryfikować wartości wejściowe.

### <a name="to-edit-an-existing-book-entry"></a>Aby edytować istniejący wpis książki

1. Wybierz wpis książki w ciągu sekundy **listy książek** sekcji. Jego bieżącej wartości powinny być wyświetlane w sekcji trzeci **Edytuj wybrane książki**.

1. Edytuj wartości za pomocą klawiatury. Najszybciej, jak albo <xref:System.Windows.Controls.TextBox> formant utraci fokus, zmiany zostaną automatycznie rozpropagowane do listy źródłowej i książki XML.

## <a name="see-also"></a>Zobacz także

[Powiązanie danych WPF za pomocą LINQ to XML — przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md)  
[Przewodnik: LinqToXmlDataBinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md)  
[Środowisko IDE programu Visual Studio — przegląd](../ide/visual-studio-ide.md)