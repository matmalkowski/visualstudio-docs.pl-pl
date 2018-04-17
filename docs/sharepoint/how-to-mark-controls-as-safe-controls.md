---
title: 'Porady: oznaczanie kontrolek pojęciem bezpiecznych kontrolek | Dokumentacja firmy Microsoft'
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
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d703beb24821663b08ed69238fcf27e2a752d64b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Porady: oznaczanie kontrolek pojęciem bezpiecznych kontrolek
  Dla bezpieczeństwa SharePoint oddzieli formantów sieci Web, które są chronione przed uruchomienie skryptu formantów sieci Web, które nie są. Chronione formantów, lub *bezpieczne kontrolki*, mogą uzyskiwać niezaufanym użytkownikom. Można oznaczyć formanty jako bezpieczne właściwości bezpieczne wpisy kontroli elementu projektu SharePoint lub w **projektanta pakietów** po dodaniu zestawu do pakietu. Aby uzyskać więcej informacji, zobacz artykuł  
  
 [plik Web.config zmiana ustawień](http://go.microsoft.com/fwlink/?LinkId=178965) i [rejestrowanie w zestawie części sieci Web jako formant bezpieczny](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Te procedury są celach ilustracyjnych. Oznaczanie kontrolek bezpieczne tylko wtedy, gdy masz pewność, że są one bezpieczne.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Oznaczenie bezpieczne kontrolki we właściwości wpisy kontroli bezpieczne  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Aby oznaczyć formanty jako bezpieczny lub niebezpieczny we właściwości bezpieczne wpisy kontroli  
  
1.  Tworzenie rozwiązania programu SharePoint z projektu programu Visual Web Part.  
  
2.  Dodaj formanty dwa do składnika Web part: pole tekstowe i przycisk. Pozostaw nazwy wartości domyślnych, Poletekstowe1 i Button1, odpowiednio.  
  
3.  Dodawanie dwóch wpisów do składnika Web part **bezpieczne wpisy kontroli** właściwości. Aby to zrobić, wybierz wielokropek (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) znajdujący się obok **bezpieczne wpisy kontroli** właściwości w  **Właściwości** okna.  
  
     **Bezpieczne wpisy kontroli** zostanie wyświetlone okno dialogowe.  
  
4.  W **bezpieczne wpisów kontroli** okno dialogowe Wybierz **Dodaj** przycisk dwa razy, aby dodawać dwa wpisy kontroli bezpieczne, aby **członków** okienko: jeden dla przycisku i jeden dla pola tekstowego.  
  
5.  Wybierz pierwsze wpisu kontroli bezpieczne, a następnie zmień wartość jego **bezpieczne** właściwości **False**, jego **nazwy typu** właściwości **Button1**, a jego **bezpieczne skryptu przed** właściwości **False**.  
  
     Ten krok określa formantu przycisku jako kontrolkę, która jest niebezpieczne.  
  
6.  Wybierz drugie wpisu kontroli bezpieczne na liście. Pozostaw wartość jego **bezpieczne** właściwość jako **True** i ustawić jej **Nazwa typu** właściwości **Poletekstowe1** i jego **bezpieczne Przed skryptu** właściwości **True**.  
  
     Kontrolki pola tekstowego jest teraz oznaczona jako formant, który jest bezpieczne przed uruchomienie skryptu.  
  
7.  Wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Oznaczenie bezpiecznych formantów w Projektancie pakietu  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Aby oznaczyć formanty jako bezpieczny lub niebezpieczny w Projektancie pakietu  
  
1.  Tworzenie rozwiązania programu SharePoint z projektu programu Visual Web Part.  
  
2.  Dodaj formanty dwa do składnika Web part: pole tekstowe i przycisk. Pozostaw nazwy wartości domyślnych, Poletekstowe1 i Button1, odpowiednio.  
  
     Zwróć uwagę, przestrzeni nazw kontrolki, ponieważ jest ona używana później.  
  
3.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie** Aby skompilować projekt.  
  
4.  Utwórz innego rozwiązania programu SharePoint.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku Package.Package, a następnie wybierz **Otwórz** otworzyć **projektanta pakietów**.  
  
6.  W **projektanta pakietów**, wybierz **zaawansowane** kartę.  
  
7.  W obszarze **dodatkowe zestawy**, wybierz **Dodaj** przycisk, a następnie wybierz pozycję **Dodawanie istniejącego zestawu** z listy.  
  
8.  W **Dodawanie istniejącego zestawu** okno dialogowe, wybierz wielokropek (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) znajdujący się obok  **Ścieżka źródłowa**.  
  
9. Wybierz zestaw z rozwiązania programu SharePoint, który został utworzony w kroku 1, a następnie wybierz **Otwórz** przycisku.  
  
10. W tym przykładzie należy pozostawić **cel wdrożenia** opcję GlobalAssemblyCache.  
  
     Ten krok powoduje, że zestaw do wdrażania na komputerze globalnej pamięci podręcznej zestawów (GAC). Jeśli chcesz, aby zestaw do wdrażania w sieci Web folderu aplikacji (Bin), należy wybrać tę opcję. Aby uzyskać więcej informacji, zobacz [wdrażanie części sieci Web w programie SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. W **bezpieczne kontrolki** wybierz **kliknij tutaj, aby dodać nowy element** przycisku.  
  
12. Wprowadź wartości dla właściwości z poniższej tabeli.  
  
    |Nazwa właściwości|Wartość|  
    |-------------------|-----------|  
    |Przestrzeń nazw|Poprawną przestrzeń nazw dla formantu, takich jak **BdcModelProject1.VisualWebPart1**.|  
    |Nazwa typu|Button1|  
    |Nazwa zestawu|Zestawu strong name, takich jak: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Bezpieczne|Wyczyść **bezpieczne** pole wyboru.|  
    |Bezpieczne względem skryptu|Pozostaw **bezpieczne skryptu przed** wyczyść pole wyboru.|  
  
    > [!NOTE]  
    >  **Nazwy zestawu** wartość dla zestawów dodane za pośrednictwem **zaawansowane** karty **projektanta pakietów** nie może być token, musi być to zestaw o silnej nazwie. Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Wybierz klawisz Tab, aby utworzyć inną wpisu kontroli bezpieczne.  
  
14. Wybierz **kliknij tutaj, aby dodać nowy element** przycisk ponownie.  
  
15. Wprowadź wartości dla właściwości z poniższej tabeli.  
  
    |Nazwa właściwości|Wartość|  
    |-------------------|-----------|  
    |Przestrzeń nazw|Poprawną przestrzeń nazw dla formantu, takich jak **BdcModelProject1.VisualWebPart1**.|  
    |Nazwa typu|Poletekstowe1|  
    |Nazwa zestawu|Zestawu strong name, takich jak: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Bezpieczne|Wybierz **bezpieczne** pole wyboru.|  
    |Bezpieczne względem skryptu|Wybierz **bezpieczne skryptu przed** pole wyboru.|  
  
16. Wybierz klawisz Tab, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Opakowanie i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  