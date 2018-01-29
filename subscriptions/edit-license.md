---
title: "Edytować subskrypcje w portalu administratora | Dokumentacja firmy Microsoft"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can edit subscription assignments.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 120bf87ddbaf50efa1abe59bac1c2e4616db7737
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="editing-visual-studio-subscription-assignments"></a>Edytowanie przypisania subskrypcji programu Visual Studio

## <a name="making-changes-to-subscriber-information"></a>Wprowadzanie zmian do subskrybenta informacji
Można edytować informacje abonenta naprawić błędy lub zaktualizować informacje. 
**Należy pamiętać, że Edycja adres e-mail subskrybenta spowoduje, że wszelkie istniejące korzyści zostaną zresetowane.**

Aby edytować subskrybenta, wybierz wielokropek (...), które są wyświetlane obok abonenta adresu e-mail, po wskaźnika myszy nad nim. Pojawi się listy rozwijanej.  Wybierz **Edytuj** Aby zmodyfikować szczegóły abonenta. Możesz również kliknąć dwukrotnie w wierszu abonenta w siatce, aby otworzyć okno edycji.

   ![Wybierz subskrybenta do edycji](_img\edit-license\select-subscriber.png)

Można aktualizować abonenta imię, nazwisko, kraj, język i pliki do pobrania. Edytuj informacje abonenta, a następnie kliknij przycisk **zapisać**.

   ![Edytuj szczegóły subskrybenta](_img\edit-license\edit-subscriber.png)

> [!NOTE]
> Jeśli potrzebujesz zmienić poziom subskrypcji dla subskrybenta, należy usunąć użytkownika z portalu i dodać je ponownie. Poziomy subskrypcji jest niemożliwa.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Edytowanie wielu subskrybentów za pomocą edycji zbiorczej

Można edytować wielu subskrybentów jednocześnie przy użyciu procesu zbiorczego edycji. Ta funkcja jest głównie używana dla organizacji, które są pośrednictwa firmowej poczty e-mail zmiany adresu lub jeśli podjęto decyzję o ograniczanie dostępu do plików do pobrania dla organizacji. 

> [!IMPORTANT]
> Poziomy subskrypcji (tj. Enterprise, Professional, itp.) i nie można zmienić subskrypcji identyfikatorów GUID.  Przy próbie przekazania z następującymi elementami zmienić przekazywania zakończy się niepowodzeniem.  

1.  Aby edytować wielu subskrybentom naraz, przejdź do karty subskrybentów. Na Wstążce u góry kliknij **zbiorczo edytować**. 

    ![Edytowanie licencji - edycji zbiorczej](_img\edit-license\edit-license-bulk-edit.png)

2.  Edycji zbiorczej używa szablonu programu Excel, aby wprowadzić zmiany w informacjach subskrybenta. W polu edycji zbiorczej kliknij **eksportu programu excel to** pobrać bieżącą listę subskrybentów wszystkie informacje o tym. 

    ![Edytowanie licencji - eksportu zbiorczego edytuje listy](_img\edit-license\edit-license-bulk-edit-export.png)

3.  Następnie należy lokalnie Zapisz plik aby można było łatwo ją znaleźć i wprowadź niezbędne zmiany przed przesłaniem go. Aby zagwarantować pomyślne przekazywania **nie były edytowane poziomie subskrypcji lub identyfikator GUID** jak będzie to spowodować niepowodzenie przekazywania. 

4.  Powrócić do portalu Visual Studio subskrypcje administracyjnej i w oknie dialogowym zbiorczo edytować, kliknij przycisk **Przeglądaj**. Wybierz zapisany plik programu Excel i kliknij przycisk **OK**. Na ekranie pojawi się postępu przekazywania.

    ![Edytowanie licencji — Edycja zbiorcza przekazywania pliku](_img\edit-license\edit-license-bulk-file-upload1.png)

5.  Po przesłaniu pliku pojawi się powiadomienie informujące, że było pomyślne. 

    ![Edytowanie licencji — Edycja zbiorcza przekazywania ukończone](_img\edit-license\edit-license-bulk-upload-complete.png)


