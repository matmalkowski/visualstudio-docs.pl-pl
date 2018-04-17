---
title: Właściwości wyświetlania siatki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 279450126cfcc7edba9398632e20bfb75e312b89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="properties-display-grid"></a>Właściwości wyświetlania siatki
**Właściwości** wyświetlane pola w obrębie siatki. Lewa kolumna zawiera nazwy właściwości; prawa kolumna zawiera wartości właściwości.  
  
## <a name="working-with-the-grid"></a>Praca z siatki  
 Lista dwie kolumny zawiera właściwości niezależny od konfiguracji, które można zmienić w czasie projektowania i ich bieżące ustawienia. Należy pamiętać, że wszystkie właściwości nie mogą być wyświetlane. Właściwość można ustawić jako ukryty, na przykład, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody. W szczególności do ukrywanie właściwości, które mają właściwości podrzędnej:  
  
1.  Ustaw `pfDisplay` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> do `FALSE`.  
  
2.  Ustaw `pfHide` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> do `TRUE`.  
  
 Aby wypychania informacji do **właściwości** używa IDE okna, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest wywoływana przez VSPackages dla każdego okna zawierającego wybieranych obiekty powiązane właściwości mają być wyświetlane w **właściwości** okna. **Eksplorator rozwiązań**w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wywołania `GetProperty` przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> w hierarchii projektu do uzyskania przeglądane obiektów w hierarchii.  
  
 Jeśli nie obsługuje VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, IDE próbuje użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> przy użyciu wartości dla <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> podać hierarchii element lub elementy.  
  
 Pakiet VSPackage nie jest konieczne tworzenie projektu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ponieważ pakietu dostarczony IDE okna implementującej go (na przykład **Eksploratora rozwiązań**) tworzy <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jej imieniu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> składa się z trzech metod, które są nazywane IDE:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> zawiera liczbę obiektów wybrane do wyświetlenia w **właściwości** okna.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Zwraca `IDispatch` obiektów, które są wybrane do wyświetlenia w **właściwości** okna.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> Umożliwia obiekty zwrócone przez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> wybranych przez użytkownika. Dzięki temu pakiet VSPackage wizualnie zaktualizować zaznaczenie jest wyświetlony dla użytkownika w interfejsie użytkownika.  
  
 **Właściwości** okna wyodrębnia dane z `IDispatch` obiektów można pobrać właściwości przeglądanie. Przeglądarka właściwości używa `IDispatch` poprosić obiektu właściwości, które obsługuje badając `ITypeInfo`, jest uzyskiwany z `IDispatch::GetTypeInfo`. Następnie używa tych wartości do wypełniania w przeglądarce **właściwości** okno i zmień wartości dla poszczególnych właściwości wyświetlane w siatce. Informacje właściwości są obsługiwane w ramach danego obiektu.  
  
 Ponieważ zwracanych obiektów obsługuje `IDispatch`, wywołujący można uzyskać informacje, takie jak nazwy obiektu wywołując jedną `IDispatch::Invoke` lub `ITypeInfo::Invoke` o identyfikatorze wysyłania wstępnie zdefiniowane (identyfikator DISPID) reprezentuje żądane informacje. Identyfikator DISPID zadeklarowane jest ujemna, aby upewnić się, że nie powodują konfliktów z identyfikatorami zdefiniowane przez użytkownika.  
  
 **Właściwości** okna przedstawia różne typy pól w zależności od atrybuty właściwości specyficzne dla wybranego obiektu. Te pola zawierają pola edycji, listy rozwijane i łącza do niestandardowego edytora okien dialogowych.  
  
-   Wartości zawartych w liście wyliczenia są pobierane przez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> kwerendę `IDispatch`. Klikając dwukrotnie nazwę pola lub klikając wartość i wybierając nową wartość z listy rozwijanej można zmienić wartości z listy wyliczenia w siatce właściwości. Dla właściwości, które zostały wstępnie zdefiniowane ustawienia z listy wyliczenia klikając dwukrotnie nazwę właściwości na liście właściwości przełączanie po kolei dostępnych wyborów. Wstępnie zdefiniowanych właściwości tylko dwie opcje, takie jak PRAWDA/FAŁSZ kliknij dwukrotnie nazwę właściwości, aby przełączyć między opcjami.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> jest `false`, wskazujący, że wartość została zmieniona, wartość jest wyświetlana pogrubioną czcionką. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Służy do określania, jeżeli wartość można przywrócić oryginalną wartość. Jeśli tak, można zmienić domyślną prawym przyciskiem myszy wartość i wybierając pozycję **zresetować** z menu wyświetlane. W przeciwnym razie należy ręcznie zmienić wartość domyślną. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> umożliwia lokalizowanie i Ukryj nazwy właściwości wyświetlane w czasie projektowania, ale nie ma wpływu na nazwy właściwości wyświetlane w czasie wykonywania.  
  
-   Klikając przycisk wielokropka (...) Wyświetla listę wartości właściwości, z których użytkownik może wybrać (na przykład selektora kolorów lub lista czcionki). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> udostępnia te wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)