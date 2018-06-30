---
title: 'Wskazówki: Tworzenie składnika Web Part dla SharePoint | Dokumentacja firmy Microsoft'
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
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7430b6fc2afc5af872c9f03174451a223e05b3e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120315"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Wskazówki: Tworzenie składnika web part dla SharePoint

Części sieci Web umożliwiają użytkownikom bezpośrednio modyfikować zawartość, wyglądu i zachowania stron w witrynie programu SharePoint za pomocą przeglądarki. W tym przewodniku przedstawiono sposób tworzenia składnika Web Part za pomocą **składnika Web Part** szablon elementu w Visual Studio 2010.

Składnik Web Part wyświetla pracowników w siatce danych. Użytkownik określa lokalizację pliku, który zawiera dane pracowników. Użytkownika można również filtrować siatki danych, dzięki czemu pracownicy, którzy są menedżerów znajdują się na liście tylko.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie składnika Web Part za pomocą programu Visual Studio **składnika Web Part** szablon elementu.

- Tworzenie właściwości, które można ustawić przez użytkownika części sieci Web. Ta właściwość określa lokalizację pliku danych pracownika.

- Renderowanie zawartości w elemencie Web Part przez dodawanie formantów do składnika Web Part formanty kolekcji.

- Tworzenie nowego elementu menu, określany jako *zlecenie,* wyświetlany w menu zleceń renderowanych części sieci Web. Zleceń zezwolić użytkownikowi na modyfikowanie danych wyświetlanych w części sieci Web.

- Testowanie części sieci Web w programie SharePoint.

    > [!NOTE]
    > Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio 2017 lub wersji programu Visual Studio cyklu życia zarządzania aplikacji (ALM).

## <a name="create-an-empty-sharepoint-project"></a>Utwórz pusty projekt programu SharePoint

Najpierw utwórz projekt SharePoint puste. Później, spowoduje dodanie składnika Web Part do projektu przy użyciu **składnika Web Part** szablon elementu.

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] za pomocą **Uruchom jako Administrator** opcji.

2. Na pasku mężczyzn wybierz **pliku** > **nowy** > **projektu**.

3. W **nowy projekt** okna dialogowego rozwiń **SharePoint** węźle język, który chcesz użyć, a następnie wybierz pozycję **2010** węzła.

4. W **szablony** okienku wybierz **projektu programu SharePoint 2010**, a następnie wybierz pozycję **OK** przycisku.

     **Kreator dostosowania programu SharePoint** pojawi się. Ten kreator umożliwia wybór lokacji, który będzie używany do debugowania projektu i poziom zaufania rozwiązania.

5. Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.

## <a name="add-a-web-part-to-the-project"></a>Dodaj składnik web part do projektu

Dodaj **składnika Web Part** elementu do projektu. **Składnika Web Part** elementu dodaje plik kodu składnika Web Part. Później dodasz kod do pliku kodu składnika Web Part do renderowania zawartości części sieci Web.

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

2. W **Dodaj nowy element** okna dialogowego, **zainstalowane szablony** okienku rozwiń **SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.

3. Na liście szablonów programu SharePoint, wybierz **składnika Web Part** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.

     **Składnika Web Part** element będzie wyświetlany w **Eksploratora rozwiązań**.

## <a name="rendering-content-in-the-web-part"></a>Renderowanie zawartości w składniku web part

Można określić, które kontrolki ma być wyświetlany w części sieci Web przez dodanie ich do kolekcji controls klasy części sieci Web.

1. W **Eksploratora rozwiązań**, otwórz *WebPart1.vb* (w języku Visual Basic) lub *WebPart1.cs* (w języku C#).

     Składnik Web Part pliku kodu zostanie otwarty w edytorze kodu.

2. Dodaj następujące instrukcje na początku pliku kodu składnika Web Part.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Dodaj następujący kod do `WebPart1` klasy. Ten kod deklaruje następujące pola:

    - Siatki danych do wyświetlenia pracowników w części sieci Web.

    - Tekst wyświetlany na formant, który służy do filtrowania danych siatki.

    - Etykietę, która zawiera błąd, jeśli nie można wyświetlić danych siatki danych.

    - Ciąg zawierający ścieżkę pliku danych pracownika.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Dodaj następujący kod do `WebPart1` klasy. Ten kod dodaje właściwość niestandardowa o nazwie `DataFilePath` do składnika Web Part. Właściwość niestandardowa jest właściwość, która może być ustawiona w programie SharePoint przez użytkownika. Ta właściwość pobiera i Ustawia lokalizację pliku danych XML, który jest używany do wypełniania siatki danych.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Zastąp `CreateChildControls` metodę z następującym kodem. Kod będzie wykonywał następujące zadania:

    - Dodaje Siatka danych i etykietę, którą można zadeklarować w poprzednim kroku.

    - Wiąże Siatka danych do pliku XML zawierającego dane pracownika.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Dodaj następującą metodę do `WebPart1` klasy. Kod będzie wykonywał następujące zadania:

    - Tworzy zlecenie, która jest wyświetlana w menu zleceń części sieci Web renderowanych części sieci Web.

    - Obsługuje zdarzenie, które jest wywoływane, gdy użytkownik wybierze zlecenie w menu zleceń. Ten kod filtruje listę pracowników, która jest wyświetlana w siatce danych.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testowanie składnika web part

Po uruchomieniu projektu otwiera witrynę programu SharePoint. Składnik Web Part jest automatycznie dodawany do galerii składników Web Part w programie SharePoint. Składnik Web Part można dodać do dowolnej strony składnika Web Part.

1. Wklej następujący kod XML w pliku Notatnika. Ten plik XML zawiera przykładowe dane, która będzie wyświetlana w składniku Web Part.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. W programie Notatnik, na pasku menu wybierz **pliku** > **Zapisz jako**.

3. W **Zapisz jako** okna dialogowego, **Zapisz jako typ** wybierz **wszystkie pliki**.

4. W **nazwę pliku** wprowadź **data.xml**.

5. Wybierz za pomocą dowolnego folderu **Przeglądaj foldery** przycisk, a następnie wybierz pozycję **zapisać** przycisku.

6. W programie Visual Studio, wybierz **F5** klucza.

     Otwieranie witryny programu SharePoint.

7. Na **Akcje witryny** menu, wybierz **więcej opcji**.

8. W **Utwórz** wybierz pozycję **strony składników Web Part** typu, a następnie wybierz **Utwórz** przycisku.

9. W **nowej strony składników Web Part** strony, nazwy strony **SampleWebPartPage.aspx**, a następnie wybierz pozycję **Utwórz** przycisku.

     Zostanie wyświetlona strona części sieci Web.

10. Wybierz wszystkie strefy na stronie składnika Web Part.

11. W górnej części strony, wybierz **Wstaw** karcie, a następnie wybierz pozycję **składnika Web Part** przycisku.

12. W **kategorii** okienku wybierz **niestandardowy** folderu, wybierz **WebPart1** składnika Web Part, a następnie wybierz **Dodaj** przycisku.

     Składnik Web Part jest wyświetlany na stronie.

## <a name="test-the-custom-property"></a>Testowanie właściwości niestandardowej

Zapełnić siatkę danych, która pojawia się w części sieci Web, określ ścieżkę pliku XML, który zawiera dane dotyczące każdego pracownika.

1. Wybierz strzałkę, która pojawia się po prawej stronie składnika Web Part, a następnie wybierz **Edytuj składnik Web Part** w menu.

     W prawej części strony zostanie wyświetlone okienko, który zawiera właściwości części sieci Web.

2. W okienku rozwiń **różne** węzła, wprowadź ścieżkę pliku XML, który został utworzony wcześniej, wybierz **Zastosuj** przycisk, a następnie wybierz pozycję **OK** przycisku.

     Sprawdź, czy w części sieci Web zostanie wyświetlona lista pracowników.

## <a name="test-the-web-part-verb"></a>Testowanie zlecenia części sieci web

Pokazywanie i ukrywanie pracownicy, którzy nie są menedżerów klikając elementu, który jest wyświetlany w menu zleceń składnika Web Part.

1. Wybierz strzałkę, która pojawia się po prawej stronie składnika Web Part, a następnie wybierz **Pokaż tylko menedżerów** w menu.

     Tylko pracownicy, którzy są menedżerów pojawiają się w części sieci Web.

2. Wybierz strzałkę ponownie, a następnie wybierz **Pokaż wszyscy pracownicy** w menu.

     Wszyscy pracownicy pojawiają się w części sieci Web.

## <a name="see-also"></a>Zobacz także

[Tworzenie składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Porady: Tworzenie składnika web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Porady: Tworzenie składnika web part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[Wskazówki: Tworzenie składnika web part dla SharePoint za pomocą projektanta](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
