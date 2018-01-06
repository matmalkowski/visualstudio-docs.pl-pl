---
title: "Porady: tworzenie i uruchamianie przykład LinqToXmlDataBinding | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dfc526651c92dd4d7ed8c93cc228fd3e75f2b3b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Porady: tworzenie i uruchamianie przykład LinqToXmlDataBinding
W tym temacie przedstawiono sposób tworzenia i kompilowania projektu programu Visual Studio LinqToXmlDataBinding i uruchamiania programu przykładzie wynikowa LinqToXmlDataBinding Windows Presentation Foundation (WPF).  
  
 Aby uzyskać więcej informacji o korzystaniu z programu Visual Studio do tworzenia projektów, zobacz [programowanie aplikacji w programie Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Tworzenie i wypełnianie projektu  
  
#### <a name="to-create-the-starting-project"></a>Aby utworzyć projekt początkowy  
  
1.  Uruchom program Visual Studio i utworzyć aplikację WPF C# o nazwie LinqToXmlDataBinding. Projekt musi korzystać z programu .NET Framework 3.5 (lub nowszej).  
  
2.  Jeśli nie jest jeszcze nie istnieje, dodaj odwołania do projektu dla następujących zestawów platformy .NET:  
  
    -   Dane systemowe  
  
    -   System.Data.DataSetExtensions  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Skompiluj rozwiązanie, naciskając klawisz **Ctnrl + Shift + B**, uruchom go przez naciśnięcie przycisku **F5**. Projekt należy skompilować bez błędów i Uruchom jako ogólnego aplikacji WPF.  
  
#### <a name="to-add-custom-code-to-the-project"></a>Aby dodać kod niestandardowy do projektu  
  
1.  W Eksploratorze rozwiązań Zmień nazwę pliku źródłowego Window1.xaml na L2XDBForm.xaml. Plik źródłowy zależnych Window1.xaml.cs powinny zostać zmienione automatycznie do L2XDBForm.xaml.cs.  
  
2.  Zastąp kod źródłowy znaleziono w pliku L2XDBForm.xaml z sekcji kod z tematu [kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). (Aby pracować z tego pliku, użyj widoku kodu XAML).  
  
3.  Podobnie, Zastąp kod w źródła w L2XDBForm.xaml.cs [kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
4.  W pliku App.xaml Zastąp wszystkie wystąpienia ciągu "Window1.xaml" z "L2XDBForm.xaml".  
  
5.  Tworzenie rozwiązania naciśnięcie **Ctrl + Shift + B**.  
  
## <a name="running-the-program"></a>Uruchomienie programu  
 LinqToXmlDataBinding program umożliwia użytkownikowi wyświetlanie i manipulowanie listę książek są przechowywane jako osadzonego elementu XML.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>Uruchom program i wyświetlania listy książek  
  
1.  Uruchom LinqToXmlDataBinding naciskając **F5** (**Rozpocznij debugowanie**) lub **Ctrl + F5** (**uruchomić bez debugowania**). Okno programu z tytułem **za pomocą LINQ do XML powiązanie danych WPF** powinien być wyświetlany.  
  
2.  Zwróć uwagę, w górnej części interfejsu użytkownika, który wyświetla nieprzetworzonego **XML** reprezentujący listy książek. Pojawi się przy użyciu programu WPF <xref:System.Windows.Controls.TextBlock> formantu, który nie obsługuje interakcji za pomocą klawiatury lub myszy.  
  
3.  Druga sekcja pionowy, o nazwie **listy książek**, wyświetla Lista uporządkowana książek jako zwykły tekst. Używa <xref:System.Windows.Controls.ListBox> kontrolkę umożliwiającą wybór jednak za pomocą klawiatury lub myszy.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>Dodawanie i usuwanie książek z listy  
  
1.  Aby usunąć istniejącą książkę z listy, wybierz go w **listy książek** sekcji, a następnie kliknij przycisk **Usuń zaznaczone książki** przycisku. Należy zauważyć, że wpis książki została usunięta z księgi i raw listy Źródło XML.  
  
2.  Aby dodać nową książkę do listy, wprowadź wartości w **identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> formantów w ostatniej sekcji **Dodawanie nowej książki**, następnie kliknij przycisk **Dodaj Podręcznik** przycisku. Należy pamiętać, że książce jest dołączany do listy w książce i zawartości XML. Ten program nie można zweryfikować wartości wejściowe.  
  
#### <a name="to-edit-an-existing-book-entry"></a>Aby edytować istniejący wpis książki  
  
1.  Wybierz wpis książki w ciągu sekundy **listy książek** sekcji. Jego bieżącej wartości powinny być wyświetlane w sekcji trzeci **Edytuj wybrane książki**.  
  
2.  Edytuj wartości za pomocą klawiatury. Najszybciej, jak albo <xref:System.Windows.Controls.TextBox> formant utraci fokus, zmiany zostaną automatycznie rozpropagowane do listy źródłowej i książki XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych WPF za pomocą LINQ do XML przykładu](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Wskazówki: Przykład LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Programowanie aplikacji w programie Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)