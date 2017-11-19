---
title: "Testowanie dużej aplikacji przy użyciu wielu map UI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: "22"
ms.author: douge
manager: douge
ms.openlocfilehash: 0be707ec592265c75ce6e0c36954010e496ac91c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Testowanie dużej aplikacji przy użyciu wielu map UI
W tym temacie omówiono sposób użycia kodowane testy interfejsu użytkownika, gdy są testowanie dużej aplikacji przy użyciu wielu map UI.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
 Podczas tworzenia nowego kodowanego testu interfejsu użytkownika, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] framework testowania generuje kod dla testu domyślnie w <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy. Aby uzyskać więcej informacji o sposobie rejestrowania kodowanych testów interfejsu użytkownika, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) i [anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).  
  
 Wygenerowany kod dla mapy interfejsu użytkownika zawiera klasę dla każdego obiektu, który test współdziała z. Dla każdej wygenerowane metody klasę pomocnika dla parametrów metod jest generowany dla tej metody. W przypadku dużej liczby obiektów, stron i formularzy i formantów w aplikacji może zwiększyć się bardzo dużych mapy interfejsu użytkownika. Ponadto jeśli wiele osób pracuje testy, aplikacji staje się niewygodna z jednego dużego pliku mapy interfejsu użytkownika.  
  
 Przy użyciu wielu UI Map plików zapewniają następujące korzyści:  
  
-   Każda mapa może być skojarzony z podzbiorem logicznej aplikacji. Dzięki temu można łatwiej zarządzać zmiany.  
  
-   Każdego tester można pracować w sekcji aplikacji i sprawdzić ich kodu bez zakłócania innych testerów Praca w innych częściach aplikacji.  
  
-   Dodatki do interfejsu użytkownika aplikacji mogą być skalowane przyrostowo z minimalny wpływ na testy dla innych elementów interfejsu użytkownika.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Czy potrzebujesz wielu map UI  
 Tworzenie wielu map UI w każdym z tych typów sytuacjach:  
  
-   Kilka zestawów złożonych złożonych kontrolek interfejsu użytkownika, wykonujące operację logicznych, takich jak strony rejestracji w witrynie sieci Web lub strony zakupu koszyk.  
  
-   Niezależne od zestaw kontrolek, które są dostępne w różnych punktach aplikacji, takich jak Kreator z wielu stronach operacji. W przypadku złożonych szczególnie każdej stronie kreatora, można utworzyć oddzielne mapy interfejsu użytkownika dla każdej strony.  
  
## <a name="adding-multiple-ui-maps"></a>Dodawanie wielu map UI  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Aby dodać mapy interfejsu użytkownika do projektu testowego kodowanego interfejsu użytkownika  
  
1.  W **Eksploratora rozwiązań**, aby utworzyć folder w projekcie kodowanego testu interfejsu użytkownika do przechowywania wszystkie mapy interfejsu użytkownika, kliknij prawym przyciskiem myszy plik projektu kodowanego testu interfejsu użytkownika, wskaż polecenie **Dodaj** , a następnie wybierz **nowy Folder**. Można na przykład nazwy `UIMaps`.  
  
     W obszarze Projekt kodowanego testu interfejsu użytkownika zostanie wyświetlony nowy folder.  
  
2.  Kliknij prawym przyciskiem myszy `UIMaps` folderu, wskaż **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
    > [!NOTE]
    >  Musisz być w projekcie kodowanego testu interfejsu użytkownika można dodać nowej mapy kodowanego testu interfejsu użytkownika.  
  
3.  Wybierz **kodowanego interfejsu użytkownika testu mapy** z listy.  
  
     W **nazwa** wprowadź nazwę nowej mapy interfejsu użytkownika. Użyj nazwy składnika lub strony mapy będzie reprezentować, na przykład `HomePageMap`.  
  
4.  Wybierz **dodać**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Minimalizuje okno i **konstruktora kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe.  
  
5.  Rejestruj akcje pierwsza metoda i wybierz **Generuj kod**.  
  
6.  Zamknij po rejestrowane wszystkie akcje i potwierdzenia do pierwszej strony lub składnika i grupować je w metodach **konstruktora kodowanego testu interfejsu użytkownika** okno dialogowe.  
  
7.  Kontynuuj tworzenie map UI. Rejestruje akcje i potwierdzeń, grupować w metody dla każdego składnika, a następnie wygeneruj kod.  
  
 W wielu przypadkach okno najwyższego poziomu aplikacji pozostaje stała dla kreatorów, formularzy i strony. Mimo że każda mapy interfejsu użytkownika ma klasę okna najwyższego poziomu, wszystkie mapy są prawdopodobnie odnoszące się do tego samego okno najwyższego poziomu w ramach wszystkich składników aplikacji Uruchom. Kodowanego interfejsu użytkownika testy wyszukiwania dla formantów hierarchicznie od góry do dołu, począwszy od okien najwyższego poziomu, więc w aplikacji złożonych, okno rzeczywistych najwyższego poziomu można zduplikowany w każdym mapy interfejsu użytkownika. Jeśli okno rzeczywistych najwyższego poziomu jest zduplikowany, wprowadzanie wielu modyfikacji spowoduje, że w przypadku zmiany tego okna. Może to spowodować problemy z wydajnością, podczas przełączania się między mapy interfejsu użytkownika.  
  
 Aby zminimalizować ten efekt, można użyć `CopyFrom()` metody w celu zapewnienia, że nowe okno najwyższego poziomu w tym mapy interfejsu użytkownika jest taka sama jak główne okno najwyższego poziomu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest częścią klasy narzędzia, która zapewnia dostęp do poszczególnych składników oraz ich formanty podrzędne, które są reprezentowane przez klasy generowane w różnych mapy interfejsu użytkownika.  
  
 Na przykład aplikacja sieci Web o nazwie `Contoso` strony głównej, strony produktu i stronę koszyka zakupów. Każdy z tych stron udostępnianie typowych okno najwyższego poziomu czyli okna przeglądarki. Brak mapy interfejsu użytkownika dla każdej strony i klasa narzędzie ma podobny do następującego kodu:  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
