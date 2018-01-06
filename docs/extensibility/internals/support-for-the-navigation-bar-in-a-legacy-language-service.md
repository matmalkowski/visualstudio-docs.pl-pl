---
title: "Obsługa paska nawigacyjnego w starsza wersja usługi języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5e2d7ddfd4904923cbdea415fa5a0d2086cc071f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Obsługa paska nawigacyjnego w usłudze języka starsza wersja
Pasek nawigacyjny u góry widoku edytora Wyświetla typy i składniki w pliku. Typy są wyświetlane w lewym listy rozwijanej, a elementy członkowskie są wyświetlane w prawej listy rozwijanej. Po wybraniu typu karetkę znajduje się w pierwszym wierszu typu. Gdy użytkownik wybierze element członkowski, karetkę znajduje się w definicji elementu członkowskiego. Pola listy rozwijanej są aktualizowane w celu odzwierciedlenia bieżącej lokalizacji karetki.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Wyświetlanie i aktualizowanie paska nawigacyjnego  
 Do obsługi na pasku nawigacyjnym, musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy i wdrożenie <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody. Kiedy usługi języka podano okno kodu base <xref:Microsoft.VisualStudio.Package.LanguageService> tworzy wystąpienie klasy <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, który zawiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> obiekt reprezentujący okno kodu. <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Nadano nowy obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Metoda pobiera <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu. Jeśli zwrócić wystąpienia użytkownika <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> wywołania z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę, aby wypełnić wewnętrznej listy i przekazuje Twojej <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> do obiektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozwijany pasek menedżera. Listy rozwijanej paska manager, z kolei wywołuje <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metody w Twojej <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu ustanowienie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> obiekt przechowujący dwóch pasków listy rozwijanej.  
  
 Jeśli karetkę przenoszony, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> wywołania metody <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metody. Podstawowym <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> wywołania metody <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody w Twojej <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasę, aby zaktualizować stan paska nawigacyjnego. Przekaż zbiór <xref:Microsoft.VisualStudio.Package.DropDownMember> obiekty do tej metody. Każdy obiekt reprezentuje wpis w listy rozwijanej.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Zawartość paska nawigacyjnego  
 Pasek nawigacyjny zwykle zawiera listę typów i listy elementów członkowskich. Lista typów zawiera wszystkie typy dostępnych w bieżącym pliku źródłowego. Nazwy typów zawierają informacje pełne przestrzeni nazw. Poniżej przedstawiono przykładowy kod C# dwa typy:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Zostanie wyświetlona lista typów `TestLanguagePackage.TestLanguageService` i `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Lista elementów członkowskich Wyświetla dostępne elementy członkowskie typu, który jest zaznaczony na liście typów. Za pomocą powyższego przykładu kodu, jeśli `TestLanguagePackage.TestLanguageService` jest typ, który jest zaznaczone, lista elementów członkowskich zawiera prywatne elementy członkowskie `tokens` i `serviceName`. Wewnętrzna struktura `Token` nie jest wyświetlany.  
  
 Można zaimplementować lista elementów członkowskich do pogrubienie nazwę elementu członkowskiego, gdy karetkę znajduje się w nim. Elementy Członkowskie mogą być także wyświetlane w wygaszone tekstu, wskazujący, że nie znajdują się w zakresie, gdzie karetka jest ustawiana obecnie.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Włączanie obsługi paska nawigacyjnego  
 Aby włączyć obsługę paska nawigacyjnego, należy ustawić `ShowDropdownBarOption` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu `true`. Ten parametr określa <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> właściwości. Do obsługi paska nawigacyjnego, musisz zaimplementować <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu w <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.  
  
 W implementacji <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metody, jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> właściwość jest ustawiona na `true`, można powrócić <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> obiektu. Jeśli nie mają obiektu, nie zostanie wyświetlony na pasku nawigacji.  
  
 Można ustawić opcję wyświetlania na pasku nawigacji przez użytkownika, co dla tego formantu można zresetować, podczas gdy widok edytor jest otwarty. Użytkownik, musisz zamknąć i ponownie otworzyć okna edytora przed wprowadzeniem zmiany.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementowanie pomocy technicznej dla paska nawigacyjnego  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Metoda przyjmuje dwoma listami (po jednym dla każdego listy rozwijanej) i dwóch wartości reprezentujący bieżące zaznaczenie w każdej z list. Listy i wartości wyboru może być aktualizowana, w którym to przypadku <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda musi zwracać `true` aby wskazać, że listy zostały zmienione.  
  
 Jak zmieni się zaznaczenie w typach listy rozwijanej, lista elementów członkowskich trzeba zaktualizować do uwzględnienia nowego typu. Co to jest wyświetlane na liście elementy Członkowskie mogą być:  
  
-   Lista elementów członkowskich dla bieżącego typu.  
  
-   Wszystkie elementy członkowskie dostępne źródła plików, ale z wszystkich elementów członkowskich nie w bieżącym typie wyświetlane w wyszarzona tekstu. Użytkownik może wybrać członków wyszarzona, nadal mogą służyć do szybkiego nawigacji, ale kolor wskazuje, że nie są częścią aktualnie wybranego typu.  
  
 Implementacja interfejsu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody zazwyczaj wykonuje następujące czynności:  
  
1.  Pobierz listę bieżącej deklaracji dla pliku źródłowego.  
  
     Istnieje wiele sposobów, aby wypełnić listy. Jednym z podejść jest utworzenie niestandardowej metody od wersji <xref:Microsoft.VisualStudio.Package.LanguageService> klasy, która wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody z powodu analizy niestandardowych, które zwraca listę wszystkich deklaracji. Innym rozwiązaniem może być wywołać <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody bezpośrednio z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodę z powodu analizy niestandardowych. Trzeci podejście może być w pamięci podręcznej deklaracje w <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy zwrócony przez ostatnią operację pełnej analizy w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i pobierania z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.  
  
2.  Wypełnij lub zaktualizować listę typów.  
  
     Zawartość listy typów może zostać zaktualizowany, gdy źródła został zmieniony lub jeśli chcesz zmienić style tekstu typów oparte na bieżącym położeniu karetki. Należy pamiętać, że w tym miejscu są przekazywane do <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.  
  
3.  Określ typ zaznacz na liście typy oparte na bieżącym położeniu karetki.  
  
     Wyszukaj deklaracje, które zostały uzyskane w kroku 1 można znaleźć typu, który umieszcza w bieżącym położeniu karetki i następnie odszukaj na liście typów dla tego typu w celu ustalenia jego indeksu na liście typów.  
  
4.  Wypełnij lub zaktualizować listy członków na podstawie wybranego typu.  
  
     Lista elementów członkowskich odzwierciedla co to jest aktualnie wyświetlany w **członków** listy rozwijanej. Zawartość listy elementów członkowskich może muszą zostać zaktualizowane, jeśli źródło uległo zmianie lub są wyświetlane tylko do elementów członkowskich wybranego typu wybranego typu została zmieniona. Jeśli wybierzesz wyświetlić wszystkie elementy członkowskie w pliku źródłowym, style tekstu dla każdego elementu członkowskiego na liście musi zostać zaktualizowany, jeśli aktualnie wybranego typu została zmieniona.  
  
5.  Określ element członkowski, zaznacz na liście elementów członkowskich na podstawie bieżącego położenia karetki.  
  
     Wyszukiwanie deklaracje, które zostały uzyskane w kroku 1 dla elementu członkowskiego, który zawiera bieżącym położeniu karetki, a następnie wyszukaj na liście elementów członkowskich, dla tego elementu, aby określić jej indeks do listy członków.  
  
6.  Zwraca `true` Jeśli wprowadzono zmiany do listy lub zaznaczenia w dowolnej listy.