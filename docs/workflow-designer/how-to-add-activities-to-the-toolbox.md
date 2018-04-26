---
title: 'Projektant przepływu pracy — porady: dodawanie działań do przybornika'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4edb752ca64afd899ac9b3e463b9d29e4b3b68a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Porady: dodawanie działań do przybornika

Można dodawać do **przybornika** w rozwiązaniu na kilka różnych sposobów. Możesz dodać je z w ramach bieżącego projektu, odwoływać je z innego projektu lub odwoływać je z innego zestawu.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Aby dodać działanie w bieżącym projekcie

1.  Dodaj nowe niestandardowe działanie do bieżącego projektu przepływu pracy. Aby uzyskać więcej informacji na temat dodawania nowego niestandardowego działania do projektu, zobacz [porady: Dodawanie nowego elementu do projektu przepływu pracy](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Dodanie logiki niestandardowej, Twoje działania.

3.  Skompiluj projekt. Jeśli kompilacja zakończyła się pomyślnie, nową kategorię w **przybornika** o nazwie "\<*Nazwa projektu*>" jest wyświetlana z działań niestandardowych do tej kategorii.

    > [!NOTE]
    > Jeśli zresetowania przybornika działań niestandardowych zostaną usunięte, nawet jeśli rozwiązanie opiera się ponownie. Ponownie wypełnić przybornika działań niestandardowych po został zresetowany, uruchom ponownie program Visual Studio 2010.

    > [!NOTE]
    > Przybornik można wyświetlić tylko jedno działanie o danej nazwie. Jeśli dwa działania z różnych zestawów mają taką samą nazwę klasy, jest wyświetlany tylko jeden z nich.

    > [!NOTE]
    > Domena aplikacji jest współdzielona przez Edytor wystąpień; Użycie zmiennych statycznych one będzie współdzielona przez także wystąpień edytora. Jeśli nie jest zamierzone zachowanie, usługa powinien służyć do śledzenia zmiennej wystąpień. Zobacz [przy użyciu kontekstu edycji elementu modelu](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) informacji na temat korzystania z usług w projektancie.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Aby dodać działania z innego projektu

1.  Otwórz rozwiązanie, który zawiera co najmniej jeden projekt przepływu pracy i projektu biblioteki działań niestandardowych lub innego projektu przepływu pracy, który definiuje działania niestandardowego.

2.  Tworzenie oba projekty. Jeśli kompilacji zakończyły się pomyślnie nową kategorię w **przybornika** o nazwie "\<*Nazwa projektu*>" jest wyświetlana z działań niestandardowych do tej kategorii.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Aby dodać działanie do przybornika z zestawu

1.  Otwórz rozwiązanie przepływu pracy.

2.  Z **narzędzia** menu, wybierz opcję **wybierz elementy przybornika...** .

3.  W **wybierz elementy przybornika** okno dialogowe, wybierz opcję **składniki elementu System.Activities** karcie, a następnie kliknij przycisk **Przeglądaj...**  można przejść do zestawu zawierającego to niestandardowe działanie ma zostać dodany.

4.  Wybierz zestaw, a następnie kliknij przycisk **OK**. Składnik niestandardowego działania zostanie dodany do listy składników i jest automatycznie wybierany.

    1.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.

5.  Aby wyświetlić Przybornika, zaznacz **przybornika** z **widoku** menu.

6.  Niestandardowe działania zostanie wyświetlony w **przybornika** kategorii, który był aktywny przed element został dodany. Na przykład jeśli **ogólne** kategorii zostało wybrane w **przybornika** przed dodaniem elementu przybornika, działanie jest wyświetlane w obszarze **ogólne** kategorii.

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)