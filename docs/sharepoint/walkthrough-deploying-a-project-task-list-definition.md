---
title: 'Wskazówki: Wdrażanie definicji listy zadań projektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fb7f8445cf43209ffed47140b1d8d204c68eaa4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Wskazówki: Wdrażanie definicji listy zadań projektu

Ten przewodnik przedstawia sposób użycia [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] do tworzenia, dostosowywania, debugowania i wdrażania listy programu SharePoint, aby śledzić zadania projektu.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio 2017 lub wersji programu Visual Studio cyklu życia zarządzania aplikacji (ALM).

## <a name="CreatingListDef"></a> Tworzenie listy programu SharePoint

Utwórz projekt listy programu SharePoint i skojarz definicji listy zadań.

1. Otwórz **nowy projekt** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.

2. W **szablony** okienku wybierz **projektu programu SharePoint 2010** szablonu, nazwy projektu **ProjectTaskList**, a następnie wybierz pozycję **OK**przycisku.

     **Kreator dostosowania programu SharePoint** pojawi się.

3. Określ lokalnej witryny programu SharePoint, którego używasz do debugowania, wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisku.

4. Otwórz menu skrótów projektu, a następnie wybierz pozycję **Dodaj**, **nowy element**.

5. W **szablony** okienku wybierz **listy** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.

     **Kreator dostosowania programu SharePoint** pojawi się.

6. W **jaką nazwę chcesz wyświetlić listy?** wprowadź **listy zadań projektu**.

7. Wybierz **Utwórz listę nie można dostosowywać na podstawie typu listy istniejących** przycisk opcji, a następnie na liście, wybierz **zadania**, a następnie wybierz pozycję **Zakończ** przycisk.

     Lista funkcji i pakietu są wyświetlane w **Eksploratora rozwiązań**.

## <a name="AddEventRcvr"></a> Dodawanie odbiorcy zdarzeń

Na liście zadań można dodać obsługiwanego odbiornika, który automatycznie ustawia ukończenia daty i opis zadania. Poniższa procedura dodaje obsługi zdarzenia prostego do wystąpienia listy jako odbiornik zdarzeń.

1. Otwórz menu skrótów węzła projektu, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy element**.

2. Na liście szablonów programu SharePoint, wybierz **odbiorcy zdarzeń** szablonu i nadaj mu nazwę **ProjectTaskListEventReceiver**.

     **Kreator dostosowania programu SharePoint** pojawi się.

3. Na **wybierz ustawienia odbiorcy zdarzeń** wybierz pozycję **zdarzenia elementu listy** jako typ odbiornika zdarzeń w **odbiornika zdarzeń typ** listy.

4. W **elementu powinien być źródło zdarzenia** wybierz **zadania**.

5. Na liście zdarzeń w celu obsługi, zaznacz pole wyboru **dodano element**, a następnie wybierz pozycję **Zakończ** przycisku.

     Nowy węzeł odbiorcy zdarzeń zostanie dodany do projektu z pliku kodu, o nazwie **ProjectTaskListEventReceiver**.

6. Dodaj kod, aby `ItemAdded` metody w **ProjectTaskListEventReceiver** pliku kodu. Zawsze nowe zadanie zostanie dodany, domyślne termin płatności i opis jest dodawany do zadania. Domyślnie powodu Data jest 1 lipca 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="CustomizeFeature"></a> Dostosowywanie funkcji listy zadań projektu

Po utworzeniu rozwiązania SharePoint Visual Studio automatycznie tworzy funkcje domyślne elementy projektu. Ustawienia listy zadań projektu witryny programu SharePoint można dostosować przy użyciu narzędzia Projektant funkcji.

1. W **Eksploratora rozwiązań**, rozwiń węzeł **funkcji**.

2. Otwórz menu skrótów **Feature1**, a następnie wybierz pozycję **Widok projektanta**.

3. W **tytuł** wprowadź **funkcja listy zadań projektu**.

4. W **zakres** wybierz **Web**.

5. W **właściwości** okna, wprowadź **1.0.0.0** jako wartość **wersji** właściwości.

## <a name="CustomizePackage"></a> Dostosowywanie pakiet listy zadań projektu

Podczas tworzenia projektu programu SharePoint, Visual Studio automatycznie dodaje funkcje, które zawierają domyślne elementy projektu do pakietu. Ustawienia listy zadań projektu witryny programu SharePoint można dostosować przy użyciu projektanta pakietów.

1. W **SolutionExplorer**, otwórz menu skrótów **pakietu**, a następnie wybierz pozycję **Widok projektanta**.

2. W **nazwa** wprowadź **ProjectTaskListPackage**.

3. Wybierz **resetowania serwera sieci Web** pole wyboru.

## <a name="BuildTest"></a> Tworzenie i testowanie listy zadań projektu

Po uruchomieniu projektu otwiera witrynę programu SharePoint. Jednak należy ręcznie przejdź do lokalizacji listy zadań.

1. Wybierz klawisz F5, aby skompilować i wdrożyć listy zadań projektu.

     Otwieranie witryny programu SharePoint.

2. Wybierz **Home** kartę.

3. Na pasku bocznym po lewej stronie, wybierz **listy zadań projektu** łącza.

     Zostanie wyświetlona strona listy zadań projektu.

4. W **narzędzia listy** , wybierz pozycję **elementów** kartę.

5. W **elementów** grupy, wybierz **nowy element** przycisku.

6. W **tytuł** tekst wprowadź **Task1**.

7. Wybierz **zapisać** przycisku.

     Po odświeżeniu lokacji **Task1** zostanie wyświetlone zadanie z terminem 2009-7-1.

8. Wybierz **Task1**.

     Zostanie wyświetlony widok szczegółowy zadania i zawiera opis "Jest zadanie krytyczne".

## <a name="Deploy"></a> Wdrażanie listy zadań projektu

Po utworzeniu i przetestować projekt listy zadań można wdrożyć na *systemu lokalnego* lub *systemu zdalnego*. System lokalny jest tym samym komputerze, na którym utworzono rozwiązania, system zdalny jest innym komputerze.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Aby wdrożyć system lokalny listy zadań projektu

Na pasku menu programu Visual Studio wybierz **kompilacji**, **wdrożyć rozwiązanie**.

Visual Studio odtwarzania puli aplikacji usług IIS, wycofuje wszystkie istniejące wersje rozwiązania kopiuje plik pakietu (wsp) rozwiązania programu SharePoint i następnie aktywuje jego funkcje. Można teraz używać rozwiązania w programie SharePoint. Aby uzyskać więcej informacji na temat kroków konfiguracji wdrażania, zobacz [porady: edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Aby wdrożyć projekt listy zadań do systemu zdalnego

1. Na pasku menu programu Visual Studio wybierz **kompilacji**, **publikowania**.

2. W **publikowania** oknie dialogowym wybierz **publikowanie w systemie plików** przycisk opcji.

     Można zmienić w lokalizacji docelowej **publikowania** okno dialogowe, wybierając przycisk wielokropka ![ikoną wielokropka](../sharepoint/media/ellipsisicon.gif "ikoną wielokropka") , a następnie przejść do innej lokalizacji.

3. Wybierz **publikowania** przycisku.

     Plik wsp jest tworzony dla rozwiązania.

4. Skopiuj plik wsp do systemu zdalnego programu SharePoint.

5. Użyj programu PowerShell `Add-SPUserSolution` polecenie, aby zainstalować pakiet w zdalnej instalacji programu SharePoint. (Dla rozwiązania farmy, należy użyć `Add-SPSolution` polecenia.)

     Na przykład `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Użyj programu PowerShell `Install-SPUserSolution` polecenia do wdrożenia rozwiązania. (Dla rozwiązania farmy, należy użyć `Install-SPSolution` polecenia.)

     Na przykład `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Aby uzyskać więcej informacji na temat zdalnego wdrażania, zobacz [przy użyciu rozwiązań](http://go.microsoft.com/fwlink/?LinkId=217680) i [Dodawanie i wdrażanie rozwiązań przy użyciu programu PowerShell w programie SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Następne kroki

Można poznać więcej informacji o sposobie dostosowywania i wdrażania rozwiązań programu SharePoint z poniższych tematów:

- [Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)

- [Program Windows PowerShell dla programu SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Zobacz też

[Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)