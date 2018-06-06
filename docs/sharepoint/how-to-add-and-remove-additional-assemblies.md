---
title: 'Porady: Dodawanie i usuwanie zestawów dodatkowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ddfdc09f27d5c94445064c064772e812779dcf08
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767780"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Porady: Dodawanie i usuwanie zestawów dodatkowych
  Jeśli pakiet programu SharePoint jest zależny od innych zestawów dla funkcji lub danych, możesz dodać zestawy do pakietu rozwiązań (wsp). W ten sposób programu SharePoint server upewnia się, że niestandardowe zestawy są instalowane przy użyciu pakietu.  
  
 Można również dodawać i zmienić bezpieczne kontrolki i klasa zasobów plików skojarzonych z zestawów.  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>Dodawanie następującej liczby dodatkowych zestawów, bezpieczne kontrolki i klasa zasobów  
 Możesz dodać dodatkowe zestawy do pakietu rozwiązania programu SharePoint. Dodatkowe zestawy w trybie piaskownicy rozwiązania wdrożyć w globalnej pamięci podręcznej zestawów, ale w trybie piaskownicy rozwiązania SharePoint — elementy projektu zostaną dodane do bazy danych zawartości. Bezpieczne kontrolki i klasa zasobów można również dodać do tych zestawów dodatkowych. Aby uzyskać więcej informacji na temat bezpiecznych formantów, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) lub "Tworzenie SafeControl — wpis" w [wdrażanie części sieci Web w programie SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Aby dodać istniejący zestaw  
  
1.  Otwórz **pakietu projektanta**. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wybierz **zaawansowane** kartę.  
  
3.  Wybierz **Dodaj** przycisk, a następnie wybierz pozycję **Dodawanie istniejącego zestawu** z listy.  
  
     **Dodawanie istniejącego zestawu** zostanie wyświetlone okno dialogowe.  
  
4.  Wybierz wielokropek (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")), a następnie wybierz zestaw, który chcesz dodać. Zalecamy używanie ścieżka względna do zestawu wybranych na potrzeby przenoszenia.  
  
5.  Dla **cel wdrożenia**, wybierz **GlobalAssemblyCache** przycisk opcji, aby wdrożyć zestawu w pamięci podręcznej GAC, lub wybierz pozycję **WebApplication** opcji Aby wdrożyć zestawu do folderu aplikacji sieci Web na serwerze z programem SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Aby dodać zestaw z danych wyjściowych projektu  
  
1.  Otwórz **pakietu projektanta**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wybierz **zaawansowane** kartę.  
  
3.  Wybierz **Dodaj** przycisk, a następnie wybierz pozycję **dodać zestawu z danych wyjściowych projektu** z listy.  
  
     **Dodać zestawu z danych wyjściowych projektu** zostanie wyświetlone okno dialogowe.  
  
4.  W **projekt źródłowy** listy, a następnie wybierz projekt źródłowy, który chcesz dodać.  
  
5.  Dla **cel wdrożenia**, wybierz **GlobalAssemblyCache** przycisk opcji, aby wdrożyć zestawu w pamięci podręcznej GAC, lub wybierz pozycję **WebApplication** opcji Aby wdrożyć zestawu do folderu aplikacji sieci Web na serwerze z programem SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Aby dodać kontrolkę bezpieczne  
  
1.  Otwórz **edytowanie istniejącego zestawu** okno dialogowe. W tym celu otwórz projektanta pakietów, wybierz pozycję **zaawansowane** karcie, wybierz zestaw, a następnie wybierz pozycję **Edytuj**przycisku.  
  
2.  W **bezpieczne kontrolki** okienku wybierz **kliknij tutaj, aby dodać nowy element** przycisku.  
  
3.  W **nazwy zestawu** kolumny, wprowadź nazwę zestawu.  
  
4.  W **Namespace** kolumny, wprowadź nazwę przestrzeni nazw kontrolki bezpieczne.  
  
5.  W **nazwy typu** kolumny, wprowadź nazwę typu.  
  
#### <a name="to-add-a-class-resource"></a>Aby dodać zasób klasy  
  
1.  Otwórz **edytowanie istniejącego zestawu** okno dialogowe. W tym celu otwórz projektanta pakietów, wybierz pozycję **zaawansowane** karcie, wybierz zestaw, a następnie wybierz pozycję **Edytuj** przycisku.  
  
2.  W **zasobów klasy** okienku wybierz **kliknij tutaj, aby dodać nowy element** przycisku.  
  
3.  W **nazwę pliku** kolumny, wybierz wielokropek (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) i wybierz zasób klasy, do którego chcesz dodać.  
  
## <a name="deleting-custom-assemblies"></a>Usuwanie zestawów niestandardowych  
 Usuwanie zestawów z pakietu programu SharePoint lub usunąć bezpieczne kontrolki i klasa zasobów z istniejących zestawów.  
  
#### <a name="to-delete-an-existing-assembly"></a>Aby usunąć istniejący zestaw  
  
1.  Otwórz **pakietu projektanta**. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Wybierz **zaawansowane** kartę.  
  
3.  W **dodatkowe zestawy** okienku wybierz niestandardowego zestawu, który chcesz usunąć.  
  
4.  Wybierz **usunąć** przycisku.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Aby usunąć formant bezpieczny dla zestawu  
  
1.  Otwórz **edytowanie istniejącego zestawu** okno dialogowe. W tym celu otwórz projektanta pakietów, wybierz pozycję **zaawansowane** karcie, wybierz zestaw, a następnie wybierz pozycję **Edytuj** przycisku.  
  
2.  Wybierz bezpieczne formant, który chcesz usunąć.  
  
3.  Wybierz klawisz Delete.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Aby usunąć zasób klasy dla zestawu  
  
1.  Otwórz **edytowanie istniejącego zestawu** okno dialogowe. W tym celu otwórz projektanta pakietów, wybierz pozycję **zaawansowane** karcie, wybierz zestaw, a następnie wybierz pozycję **Edytuj** przycisku.  
  
2.  Wybierz zasób klasy, który chcesz usunąć.  
  
3.  Wybierz klawisz Delete.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
