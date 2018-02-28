---
title: Tworzenie kategorii ustawienia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2bdf3231f2df8b3700c7865fa53e60003b814a5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-settings-category"></a>Tworzenie kategorii ustawień
W tym przewodniku Utwórz kategorię ustawienia programu Visual Studio i używać go do wartości, aby zapisać i przywrócić wartości z pliku ustawień. Kategoria ustawienia jest grupą powiązane właściwości, które są wyświetlane jako "punkt ustawień niestandardowych;" oznacza to, że pole wyboru w **importowanie i eksportowanie ustawień** kreatora. (Można go znaleźć na **narzędzia** menu.) Ustawienia są zapisywane lub przywrócić jako kategorie, a poszczególne ustawienia nie są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Tworzenie kategorii ustawień przez wynikających z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy.  
  
 Aby uruchomić tego przewodnika, najpierw musisz zakończyć w pierwszej sekcji [tworzenie stron opcje](../extensibility/creating-an-options-page.md). Wynikowa Opcje siatki właściwości pozwala sprawdzić i zmienić właściwości w kategorii. Po zapisaniu kategorii właściwości w pliku ustawień, zapoznaj się z plikiem, aby zobaczyć, jak są przechowywane wartości właściwości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Tworzenie kategorii ustawień  
 W tej sekcji służy do zapisywania i przywracania wartości kategorii ustawienia punktu ustawienia niestandardowe.  
  
#### <a name="to-create-a-settings-category"></a>Aby utworzyć Kategoria Ustawienia  
  
1.  Zakończenie [tworzenie stron opcje](../extensibility/creating-an-options-page.md).  
  
2.  Otwórz plik VSPackage.resx i Dodaj zasoby te trzy parametry:  
  
    |Nazwa|Wartość|  
    |----------|-----------|  
    |106|Moje kategorii|  
    |107|Moje ustawienia|  
    |108|OptionInteger i OptionFloat|  
  
     Utworzenie zasobów w tej nazwie kategorii "Moje kategorii", "Moje ustawienia obiektu" i opis kategorii "OptionInteger i OptionFloat".  
  
    > [!NOTE]
    >  Z tych trzech nazwę kategorii nie są wyświetlane w Kreatorze importowania i eksportowania ustawień.  
  
3.  W MyToolsOptionsPackage.cs, Dodaj `float` właściwości o nazwie `OptionFloat` do `OptionPageGrid` klasy, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid` Kategoria o nazwie "My kategorii" teraz składa się z dwóch właściwości `OptionInteger` i `OptionFloat`.  
  
4.  Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> do `MyToolsOptionsPackage` klasy i nadaj mu CategoryName "Moje kategorii", nadaj ObjectName "Moje ustawienia" i isToolsOptionPage ustawioną wartość true. Ustaw categoryResourceID objectNameResourceID i DescriptionResourceID odpowiadający jej zasób ciągu utworzone wcześniej identyfikatorów.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Skompiluj projekt i Rozpocznij debugowanie. W eksperymentalnym wystąpieniu powinna zostać wyświetlona który **Moja strona siatki** ma teraz zarówno całkowitoliczbowych i zmiennoprzecinkowych wartości.  
  
## <a name="examining-the-settings-file"></a>Sprawdzenie pliku ustawień  
 W tej sekcji możesz wyeksportować do pliku ustawień wartości właściwości kategorii. Zapoznaj się z plikiem, a następnie zaimportować do tej kategorii właściwości wartości.  
  
1.  Uruchom projekt w trybie debugowania, naciskając klawisz F5. Spowoduje to uruchomienie eksperymentalne wystąpienie.  
  
2.  Otwórz **narzędzia / Opcje** okna dialogowego.  
  
3.  W widoku drzewa w lewym okienku rozwiń **Moje kategorii** , a następnie kliknij przycisk **Moja strona siatki**.  
  
4.  Zmień wartość **OptionFloat** do 3.1416 i **OptionInteger** do 12. Kliknij przycisk **OK**.  
  
5.  Na **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**.  
  
     **Import i eksport ustawień** zostanie wyświetlony Kreator.  
  
6.  Upewnij się, że **Eksportuj wybrane ustawienia środowiska** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
     **Wybierz ustawienia do eksportowania** zostanie wyświetlona strona.  
  
7.  Kliknij przycisk **Moje ustawienia**.  
  
     **Opis** zmienia się na **OptionInteger i OptionFloat**.  
  
8.  Upewnij się, że **Moje ustawienia** jest tylko kategorię, która jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
     **Nazwę pliku ustawień** zostanie wyświetlona strona.  
  
9. Nazwa nowego pliku ustawień `MySettings.vssettings` i zapisz go w odpowiednim katalogu. Kliknij przycisk **Zakończ**.  
  
     **Wyeksportować pełną** strony zgłasza, że Twoje ustawienia zostały pomyślnie wyeksportowane.  
  
10. Na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**. Zlokalizuj `MySettings.vssettings` i otwórz go.  
  
     Kategoria właściwości wyeksportowany w poniższej sekcji pliku (z identyfikatorów GUID będą się różnić) można znaleźć.  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     Należy zauważyć, że nazwa kategorii Pełna został utworzony przez dodanie znaku podkreślenia do nazwę kategorii, a następnie według nazwy obiektu. OptionFloat i OptionInteger pojawiają się w danej kategorii, wraz z ich wyeksportowanej wartości.  
  
11. Zamknij plik ustawień bez jego zmiany.  
  
12. Na **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **Moje kategorii**, kliknij przycisk **Moja strona siatki** , a następnie zmień wartość  **OptionFloat** 1.0 i **OptionInteger** do 1. Kliknij przycisk **OK**.  
  
13. Na **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**, wybierz pozycję **Importuj wybrane ustawienia środowiska**, a następnie kliknij przycisk **dalej**.  
  
     **Zapisać bieżące ustawienia** zostanie wyświetlona strona.  
  
14. Wybierz **nie, tylko zaimportuj nowe ustawienia** , a następnie kliknij przycisk **dalej**.  
  
     **Wybierz kolekcję ustawień do zaimportowania** zostanie wyświetlona strona.  
  
15. Wybierz `MySettings.vssettings` w pliku **Moje ustawienia** węzła widoku drzewa. Jeśli plik nie ma w widoku drzewa, kliknij przycisk **Przeglądaj** go odnaleźć. Kliknij przycisk **Dalej**.  
  
     **Wybierz ustawienia do importowania** zostanie wyświetlone okno dialogowe.  
  
16. Upewnij się, że **Moje ustawienia** jest zaznaczone, a następnie kliknij przycisk **Zakończ**. Gdy **pełny Import** zostanie wyświetlona strona, kliknij przycisk **Zamknij**.  
  
17. Na **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **Moje kategorii**, kliknij przycisk **Moja strona siatki** i sprawdź, czy wartości właściwości kategorii została przywrócona.