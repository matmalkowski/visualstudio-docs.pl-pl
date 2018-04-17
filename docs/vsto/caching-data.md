---
title: Buforowanie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 094a4e6c639007fcf09ce28f0be2e398b8245858
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="caching-data"></a>Buforowanie danych
  Może buforować dane obiektów w dostosowaniu poziomie dokumentu, tak, aby dane są dostępne w trybie offline lub bez konieczności otwierania programu Microsoft Office Word i Microsoft Office Excel. W pamięci podręcznej obiektu, obiekt musi mieć typ danych, który spełnia określone wymagania. Wiele typowych typów danych w programie .NET Framework spełnia te wymagania, w tym <xref:System.String>, <xref:System.Data.DataSet>, i <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Istnieją dwa sposoby dodawania obiektu do pamięci podręcznej danych:  
  
-   Aby dodać obiektu do pamięci podręcznej danych podczas tworzenia rozwiązania, należy zastosować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu deklaracji obiektu. Aby uzyskać więcej informacji, zobacz [porady: dane pamięci podręcznej do użycia w trybie Offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Aby programowo dodać obiektu do pamięci podręcznej danych w czasie wykonywania, należy użyć `StartCaching` metody hosta elementów, takich jak `ThisDocument` lub `ThisWorkbook` klasy. Aby uzyskać więcej informacji, zobacz [porady: programowane buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Po dodaniu obiektu w pamięci podręcznej danych można uzyskać dostęp i modyfikować buforowane dane bez konieczności uruchamiania programu Word i Excel. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Wymagania dotyczące obiektów danych w pamięci podręcznej  
 W pamięci podręcznej obiektu danych w rozwiązaniu, obiekt musi spełniać wymagania w zakresie:  
  
-   Można odczytu/zapisu pola publicznego lub właściwości elementu hosta, takich jak `ThisDocument` lub `ThisWorkbook` klasy.  
  
-   Nie można indeksatora lub innych sparametryzowane.  
  
 Ponadto obiekt danych musi umożliwiać serializację za pomocą <xref:System.Xml.Serialization.XmlSerializer> klasy, która oznacza, że typ obiektu musi mieć następujące cechy:  
  
-   Być typem publicznym.  
  
-   Mieć publicznego konstruktora bez parametrów.  
  
-   Nie można wykonać kod, który wymaga dodatkowych uprawnień.  
  
-   Udostępnianie tylko odczytu/zapisu właściwości publiczne (inne właściwości zostaną zignorowane).  
  
-   Nie można ujawniać tablic wielowymiarowych (tablice zagnieżdżone są akceptowane).  
  
-   Zwraca interfejsów z właściwościami i polami.  
  
-   Implementuje <xref:System.Collections.IDictionary> Jeśli kolekcji.  
  
 Gdy buforowanie obiektu danych [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializuje obiekt do ciągu XML, który jest przechowywany w *niestandardowym elementem XML* w dokumencie. Aby uzyskać więcej informacji, zobacz [przegląd części XML niestandardowe](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Limity rozmiaru danych z pamięci podręcznej  
 Istnieją pewne ograniczenia całkowitej ilości danych, które można dodać do pamięci podręcznej danych w dokumencie i rozmiar wszystkich poszczególnych obiektów w pamięci podręcznej danych. Jeśli przekroczysz te limity aplikacji mogą zostać nieoczekiwanie zamknięte podczas zapisywania danych w pamięci podręcznej danych.  
  
 Aby uniknąć tych ograniczeń, postępuj zgodnie z tymi wytycznymi:  
  
-   Nie dodawaj dowolnego obiektu większych niż 10 MB do pamięci podręcznej danych.  
  
-   Nie należy dodawać więcej niż 100 MB danych, całkowita pamięć podręczna danych w jednym dokumencie.  
  
 Są to przybliżonej wartości. Dokładne ograniczenia są zależne od kilka czynników, takich jak dostępnej pamięci RAM i liczba uruchomionych procesów.  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>Kontrolowanie zachowania buforowanych obiektów  
 Aby uzyskać większą kontrolę nad zachowanie obiektu w pamięci podręcznej, można zaimplementować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfejsu w typie obiektu w pamięci podręcznej. Na przykład można zaimplementować ten interfejs, jeśli chcesz kontrolować sposób użytkownik jest powiadamiany, gdy obiekt zostanie zmieniona. Przykłady kodu, które przedstawiają sposób wykonania <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, zobacz `ControlCollection` klasy w dynamicznych próbka formantów programu Excel i Word dynamiczne próbki formantów w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>Utrwalanie zmiany danych z pamięci podręcznej dokumenty chronione hasłem  
 Jeśli buforowanie obiektów danych w dokumencie, który jest chroniony hasłem, zmiany w pamięci podręcznej danych nie są zapisywane. Można zapisać zmian w pamięci podręcznej danych przez zastąpienie dwóch metod. Zastępować te metody umożliwiających tymczasowe usunięcie ochrony po zapisaniu dokumentu, a następnie ponownie zastosuj ochrony po zapisywania operacja została zakończona.  
  
 Aby uzyskać więcej informacji, zobacz [porady: dane pamięci podręcznej w dokumencie chronionym hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>Zapobieganie utracie danych podczas dodawania wartości Null do pamięci podręcznej danych  
 Po dodaniu obiektów do buforowania danych, wszystkie obiekty pamięci podręcznej musi być zainicjowany niż**null** wartość przed dokumentu jest zapisane i zamknięte. Jeśli ma dowolnego obiektu w pamięci podręcznej **null** wartości po zapisaniu dokumentu i zamknięte, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] spowoduje automatyczne usunięcie wszystkich obiektów w pamięci podręcznej z pamięci podręcznej danych.  
  
 Po dodaniu obiektu z **null** wartość w pamięci podręcznej danych przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu w czasie projektowania, można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> obiektów klasy zainicjować buforowane dane przed otwarciem dokumentu. Jest to przydatne, jeśli chcesz zainicjować buforowane na serwerze bez Word czy Excel zainstalowany, przed otwarciem dokumentu przez użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dane z pamięci podręcznej do użycia w trybie Offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Porady: programowane buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Porady: dane w dokumencie chroniony hasłem z pamięci podręcznej](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Przewodnik: Tworzenie relacji wzorzec/szczegół z użyciem zestawu danych z pamięci podręcznej](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  