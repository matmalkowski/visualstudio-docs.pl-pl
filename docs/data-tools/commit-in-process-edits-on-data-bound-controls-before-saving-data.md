---
title: Zatwierdź wewnątrzprocesowych na formantach powiązanych z danymi przed zapisaniem danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a0811ec9338bfb84235679a68d32169435eb57a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Zatwierdź wewnątrzprocesowych na formantach powiązanych z danymi przed zapisaniem danych

Podczas edycji wartości w formantach powiązanych z danymi, użytkownicy muszą Przejdź poza bieżącego rekordu można przekazać zaktualizowanej wartości do powiązanej z kontroli źródła danych. Gdy przeciągnij elementy z [Data Sources — okno](add-new-data-sources.md) na formularz, pierwszy element, który musisz porzucić generuje kod w **zapisać** zdarzenia kliknij przycisk <xref:System.Windows.Forms.BindingNavigator>. Ten kod wywołuje <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody <xref:System.Windows.Forms.BindingSource>. W związku z tym wywołaniu <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody są generowane tylko dla pierwszego <xref:System.Windows.Forms.BindingSource> dodana do formularza.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> Wywołania zatwierdza wszystkie zmiany, które są w trakcie w formantów powiązanych z danymi, które są aktualnie edytowany. W związku z tym, jeśli formant powiązany z danymi nadal ma fokus i użytkownik kliknie **Zapisz** przycisk wszystkie oczekujące zmiany, w tym kontroli są zaangażowane przed rzeczywiste Zapisz ( `TableAdapterManager.UpdateAll` metody).

Można skonfigurować aplikację do automatycznego zatwierdzania zmian, nawet wtedy, gdy użytkownik próbuje zapisać dane bez zatwierdzania zmian, jako część zapisu procesu.

> [!NOTE]
> Dodaje projektanta `BindingSource.EndEdit` kod tylko pierwszy element upuszczone na formularzu. W związku z tym należy dodać wiersza kodu w celu wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu. Można ręcznie dodać wiersza kodu w celu wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource>. Alternatywnie można dodać `EndEditOnAllBindingSources` metody do formularza i wywołać go przed wykonaniem zapisywania.

Poniższy kod używa [LINQ (zapytania język Language-Integrated)](/dotnet/csharp/linq/) zapytania w celu wykonania iteracji wszystkie <xref:System.Windows.Forms.BindingSource> składniki i wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aby wywołać EndEdit dla wszystkich składników BindingSource w formularzu

1.  Dodaj następujący kod do formularza, który zawiera <xref:System.Windows.Forms.BindingSource> składników.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Dodaj następujący wiersz kodu bezpośrednio przed wezwań można zapisać danych formularza ( `TableAdapterManager.UpdateAll()` metody):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)