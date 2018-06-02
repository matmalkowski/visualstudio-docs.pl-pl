---
title: Edytować subskrypcje w portalu administratora | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Dowiedz się, jak Administratorzy mogą edytować przypisania subskrypcji.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4ee209af97d09f5d7e2125d2111746f6fe491f5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34476641"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Edytowanie przypisania subskrypcji programu Visual Studio

Jako administrator subskrypcji możesz wprowadzić zmiany do subskrypcji, przypisane do osób w danej organizacji.  W tym artykule omówiono typy zmian można wprowadzać i niezbędne instrukcje. 

## <a name="making-changes-to-subscriber-information"></a>Wprowadzanie zmian do subskrybenta informacji
Można edytować informacje abonenta naprawić błędy lub zaktualizować informacje. 

Aby edytować subskrybenta, wybierz wielokropek (...), które są wyświetlane obok abonenta adresu e-mail, po wskaźnika myszy nad nim. Pojawi się listy rozwijanej.  Wybierz **Edytuj** Aby zmodyfikować szczegóły abonenta. Możesz również kliknąć dwukrotnie w wierszu abonenta w siatce, aby otworzyć okno edycji.

   <img alt="Select subscriber to edit" src="_img\edit-license\select-subscriber.png" style="border: 1px solid #CCCCCC" />
    
Można aktualizować abonenta imię, nazwisko, kraj, język i pliki do pobrania. Edytuj informacje abonenta, a następnie kliknij przycisk **zapisać**.

 
   <img alt="Edit subscriber details" src="_img\edit-license\edit-subscriber.png" style="border: 1px solid #CCCCCC" />
   > [!NOTE]
   > Jeśli potrzebujesz zmienić poziom subskrypcji dla subskrybenta, należy usunąć użytkownika z portalu i dodać je ponownie. Poziomy subskrypcji jest niemożliwa.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Edytowanie wielu subskrybentów za pomocą edycji zbiorczej

Można edytować wielu subskrybentów jednocześnie przy użyciu procesu zbiorczego edycji. Ta funkcja jest głównie używana dla organizacji, które są pośrednictwa firmowej poczty e-mail zmiany adresu lub jeśli podjęto decyzję o ograniczanie dostępu do plików do pobrania dla organizacji. 

   > [!IMPORTANT]
   > Poziomy subskrypcji (tj. Enterprise, Professional, itp.) i nie można zmienić subskrypcji identyfikatorów GUID.  Przy próbie przekazania z następującymi elementami zmienić przekazywania zakończy się niepowodzeniem.  

1.  Aby edytować wielu subskrybentom naraz, przejdź do karty subskrybentów. Na Wstążce u góry kliknij **zbiorczo edytować**. 

    <img alt="Editing a License - Bulk Edits" src="_img\edit-license\edit-license-bulk-edit.png" style="border: 1px solid #CCCCCC" />

2.  Edycji zbiorczej używa szablonu programu Excel, aby wprowadzić zmiany w informacjach subskrybenta. W polu edycji zbiorczej kliknij **eksportu programu excel to** pobrać bieżącą listę subskrybentów wszystkie informacje o tym. 

    <img alt="Editing a License - Export Bulk Edits List" src="_img\edit-license\edit-license-bulk-edit-export.png" style="border: 1px solid #CCCCCC" />

3.  Następnie należy lokalnie Zapisz plik aby można było łatwo ją znaleźć i wprowadź niezbędne zmiany przed przesłaniem go. Aby zagwarantować pomyślne przekazywania **nie były edytowane poziomie subskrypcji lub identyfikator GUID** jak będzie to spowodować niepowodzenie przekazywania. 

4.  Powrócić do portalu Visual Studio subskrypcje administracyjnej i w oknie dialogowym zbiorczo edytować, kliknij przycisk **Przeglądaj**. Wybierz zapisany plik programu Excel i kliknij przycisk **OK**. Na ekranie pojawi się postępu przekazywania.

    <img alt="Editing a License - Bulk Edits File Upload" src="_img\edit-license\edit-license-bulk-file-upload1.png" style="border: 1px solid #CCCCCC" />

5.  Po przesłaniu pliku pojawi się powiadomienie informujące, że było pomyślne. W tym momencie zmiany zostaną odzwierciedlone w informacji dotyczących subskrybenta. 

    <img alt="Editing a License - Bulk Edits Upload Complete" src="_img\edit-license\edit-license-bulk-upload-complete.png" style="border: 1px solid #CCCCCC" />

