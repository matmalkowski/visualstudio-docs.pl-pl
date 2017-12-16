---
title: "Usługi Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b73e2cf93cf0f557db072586b7aa67ab730fad4f
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio
Program Visual Studio udostępnia narzędzia do pracy z systemem Windows Communication Foundation (WCF) i [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], technologii firmy Microsoft do tworzenia aplikacji rozproszonych. Ten temat zawiera wprowadzenie do usługi z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] perspektywy. Pełną dokumentację można znaleźć [4.5 usługi danych WCF](/dotnet/framework/data/wcf/index).  
  
## <a name="what-is-wcf"></a>Co to jest WCF?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]to ujednoliconego platforma do tworzenia bezpiecznego, niezawodne, transakcyjne i interoperacyjne aplikacji rozproszonych. Zastępuje starsze technologii komunikacji międzyprocesowej, takich jak usługi sieci Web ASMX, .NET Remoting, usługi przedsiębiorstwa (DCOM) i usługi MSMQ. Usługi WCF, połączono funkcji tych technologii w ujednoliconego modelu programowania. Upraszcza to środowisko rozwoju aplikacji rozproszonych.  
  
#### <a name="what-are-wcf-data-services"></a>Co to są usługi danych WCF  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]jest to standardowy implementacji protokołu Open Data (OData).  Usługi danych WCF umożliwia udostępnianie danych tabelarycznych jako zestaw interfejsów API REST, umożliwiając zwrócić dane przy użyciu standardowych poleceń HTTP, takich jak GET, POST, PUT lub usunąć. Po stronie serwera usługi danych WCF są zastępowane przez [ASP.NET Web API](http://www.asp.net/web-api) do tworzenia nowych usług OData. Biblioteka klienta usługi danych WCF w dalszym ciągu jest dobrym rozwiązaniem w przypadku używania usługi OData w aplikacji .NET w programie Visual Studio (**projektu &#124; Dodaj odwołanie do usługi**). Aby uzyskać więcej informacji, zobacz [4.5 usługi danych WCF](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### <a name="wcf-programming-model"></a>Model programowania WCF  
 Model programowania WCF jest oparty na komunikacji między dwiema jednostkami: usługi WCF i klienta WCF. Model programowania są umieszczane w <xref:System.ServiceModel> przestrzeni nazw w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### <a name="wcf-service"></a>Usługi WCF  
 Usługa WCF jest oparta na interfejs, który definiuje kontrakt między usługą i klienta. Jest on oznaczony <xref:System.ServiceModel.ServiceContractAttribute> atrybutu, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Zdefiniuj funkcje i metody, które są udostępniane przez usługi WCF, oznaczając je za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu. Ponadto można ujawniać dane serializowane przez oznaczenie typu złożonego z <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Umożliwia to powiązanie danych w kliencie.  
  
 Po zdefiniowaniu interfejsu oraz metod jej one znajdują się w klasie, która implementuje interfejs. Jednej klasy usługi WCF można zaimplementować wiele kontraktów usług.  
  
 Usługa WCF jest widoczna dla zużycia, przez co jest nazywane *punktu końcowego*. Punkt końcowy zapewnia tylko sposób komunikowania się z usługą; nie masz dostępu do usługi za pośrednictwem bezpośrednie odwołanie tak jak w przypadku innych klas.  
  
 Punkt końcowy składa się z adresu, powiązania i kontrakt. Adres Określa, gdzie usługa znajduje się; może to być adres URL, adres FTP lub sieci lub ścieżka lokalna. Powiązanie definiuje sposób komunikacji z usługą. Powiązania WCF zapewniają elastyczne modelu określająca protokół HTTP lub FTP mechanizm zabezpieczeń, takich jak uwierzytelnianie systemu Windows lub nazwy użytkownika i hasła, na przykład i wiele innych funkcji. Kontrakt obejmuje operacje, które są dostępne w klasie usługi WCF.  
  
 Wiele punktów końcowych można uwidocznić dla jednej usługi WCF. Dzięki temu różnych klientów do komunikacji z tej samej usługi na różne sposoby. Na przykład usługi bankowości może Podaj jeden punkt końcowy dla pracowników i drugi dla klientów zewnętrznych, każdego przy użyciu innego adresu powiązanie, i/lub kontraktu.  
  
#### <a name="wcf-client"></a>Klient WCF  
 Klienta programu WCF składa się z *proxy* , który umożliwia aplikacjom komunikować się z usługą WCF i punktu końcowego, który odpowiada punkt końcowy zdefiniowany dla usługi. Serwer proxy jest generowany po stronie klienta w pliku app.config i zawiera informacje na temat typów i metod, które są udostępniane przez usługę. Dla usług, które udostępniają wiele punktów końcowych klient może wybrać jedną, która najlepiej odpowiada jego potrzebom, na przykład do komunikacji za pośrednictwem protokołu HTTP i uwierzytelniania systemu Windows.  
  
 Po utworzeniu klienta programu WCF możesz odwoływać się usługi w kodzie tak samo, jak każdy inny obiekt. Na przykład, aby wywołać `GetData` metody pokazano wcześniej, czy pisania kodu, który jest podobny do następującego:  
  
 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## <a name="wcf-tools-in-visual-studio"></a>Narzędzia WCF w programie Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]udostępnia narzędzia umożliwiające tworzenie zarówno usługi WCF i klienci WCF. Aby uzyskać wskazówki, który demonstruje narzędzi, zobacz [wskazówki: Tworzenie prostego usługi WCF w formularzach systemu Windows](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### <a name="creating-and-testing-wcf-services"></a>Tworzenie i testowanie usługi WCF  
 Można użyć usługi WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonów jako podstawę do szybkiego tworzenia własnej usługi. Host automatycznie usługi WCF i testowanie klienta WCF można następnie użyć do debugowania i testowania usługi. Te narzędzia razem zapewniają szybki i wygodny debugowania i testowania cyklu i wyeliminowanie konieczności zatwierdzenia w modelu hostingu na wczesnym etapie.  
  
#### <a name="wcf-templates"></a>Szablony programu WCF  
 Usługi WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Szablony zapewniają strukturę klasa podstawowa dla rozwoju usługi. Są dostępne w kilku szablonów WCF **Dodawanie nowego projektu** okno dialogowe. Obejmują one projekty biblioteki usługi WCF, witryn sieci Web usługi WCF i szablony element usługi WCF.  
  
 Po wybraniu szablonu pliki są dodawane do umowy serwisowej, implementacji usługi i konfiguracji usługi. Wszystkie atrybuty niezbędne są już dodane, tworzenie prostego tekstu "Hello World" usługi, a nie miał pisania kodu. Oczywiście chcesz Dodaj kod, aby zapewnić funkcje i metody dla usługi rzeczywistych, ale te szablony stanowią podstawę podstawowe.  
  
 Aby uzyskać więcej informacji o szablonach WCF, zobacz [szablony Visual Studio WCF](/dotnet/framework/wcf/wcf-vs-templates).  
  
#### <a name="wcf-service-host"></a>Host usługi WCF  
 Po rozpoczęciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugera (naciskając klawisz F5) w projekcie usługi WCF, Host usługi WCF, które są automatycznie uruchamiane jest narzędzie do obsługi usługi lokalnie. Host usługi WCF wylicza usług w projekcie usługi WCF, ładuje konfigurację projektu i tworzy wystąpienie hosta dla każdej usługi, która znajdzie.  
  
 Za pomocą Host usługi WCF, można przetestować usługi WCF bez pisania kodu dodatkowe lub zobowiązuje się do określonego hosta podczas tworzenia.  
  
 Aby dowiedzieć się więcej na temat Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).  
  
#### <a name="wcf-test-client"></a>Klienta testowego WCF  
 Narzędzia testowania klienta WCF umożliwia badanie parametrów wejściowych, przesyłanie, że dane wejściowe do usługi WCF i wyświetlić usługi odsyła odpowiedź. Umożliwia wygodne usługi testowania czynności połączenie z hostem usługi WCF. Narzędzie znajduje się w folderze \Common7\IDE, czyli dla programu Visual Studio 2015 zainstalowany w stacji dysków C: tutaj: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.  
  
 Po naciśnięciu klawisza F5 w celu debugowania projektu usługi WCF, klienta testowego WCF otwiera i wyświetla listę punktów końcowych usługi, które są zdefiniowane w pliku konfiguracji. Można przetestować parametry i uruchom usługę i powtórz ten proces, aby stale testowanie i weryfikowanie usługi.  
  
 Aby dowiedzieć się więcej na temat klienta testowego WCF, zobacz [klienta testowego WCF (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>Uzyskiwanie dostępu do usług WCF w programie Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]upraszcza zadanie tworzenia klienci WCF, automatyczne generowanie serwera proxy i punktu końcowego dla usług, które można dodać przy użyciu **Dodaj odwołanie do usługi** okno dialogowe. Wszystkie informacje o konfiguracji niezbędne są dodawane do pliku app.config. Większość czasu, wszystkie punkty, które musisz wykonać jest utworzenia wystąpienia usługi do jej używania.  
  
 **Dodaj odwołanie do usługi** okno dialogowe umożliwia wprowadź adres dla usługi lub wyszukaj usługi, która jest zdefiniowana w rozwiązaniu. Okno dialogowe zwraca listę usług i operacji dostarczonych przez tych usług. Umożliwia on również zdefiniowanie przestrzeni nazw za pomocą którego można będzie odwoływać się do usługi w kodzie.  
  
 **Skonfigurować odwołania do usług** okno dialogowe umożliwia dostosowanie konfiguracji dla usługi. Można zmienić adres usługi, określ poziom dostępu, zachowanie asynchroniczne i typy kontraktu komunikatu i konfigurować ponownego użycia typu.  
  
## <a name="how-to-select-a-service-endpoint"></a>Porady: Wybieranie punktu końcowego usługi  
Niektóre usługi Windows Communication Foundation (WCF) ujawnia wiele punktów końcowych za pomocą których klient może komunikować się z usługą. Na przykład usługa może narazić jeden punkt końcowy, który korzysta z protokołu HTTP powiązanie i nazwę użytkownika / hasło zabezpieczeń i drugiego punktu końcowego, który używa uwierzytelniania systemu Windows i FTP. Pierwszym punktem końcowym może być używany przez aplikacje, które uzyskują dostęp do usługi z poza zaporą, podczas gdy druga mogą być używane w sieci intranet.  
  
W takim przypadku można określić `endpointConfigurationName` jako parametr do konstruktora dla odwołania do usługi.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>Aby wybrać punkt końcowy usługi  
  
1.  Dodaj odwołanie do usługi WCF prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierając pozycję **dodać odwołania do usługi**.
  
2.  W edytorze kodu, dodaj konstruktor dla odwołania do usługi:  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Zastąp *servicereference kierowany* z przestrzenią nazw dla odwołania do usługi i Zamień *Service1Client* o nazwie usługi.  
  
3.  Zostanie wyświetlona lista IntelliSense z przeciążeń dla konstruktora. Wybierz `endpointConfigurationName As String` przeciążenia.  
  
4.  Następujące przeciążenia, wpisz `=` *ConfigurationName*, gdzie *ConfigurationName* to nazwa punktu końcowego, który ma być używany.  
  
    > [!NOTE]
    >  Jeśli nie znasz nazwy dostępnych punktów końcowych, można je znaleźć w pliku app.config.  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Aby znaleźć dostępnych punktów końcowych dla usługi WCF  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik app.config dla projektu, który zawiera odwołania do usługi, a następnie kliknij przycisk **Otwórz**. Plik zostanie wyświetlony w edytorze kodu.  
  
2.  Wyszukaj `<Client>` znacznika w pliku.  
  
3.  Wyszukaj poniżej `<Client>` tag znacznika, który rozpoczyna się od `<Endpoint>`.  
  
     Jeśli usługa zawiera wiele punktów końcowych, będzie co najmniej dwa `<Endpoint` tagów.  
  
4.  Wewnątrz `<EndPoint>` tag znajdziesz `name="` *SomeService* `"` parametr (gdzie *SomeService* reprezentuje nazwę punktu końcowego). Jest to nazwa dla punktu końcowego, które mogą zostać przekazane do `endpointConfigurationName As String` przeciążenia konstruktora dla odwołania do usługi.  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>Porady: asynchroniczne wywoływanie metody usługi  
Większości metod w usługach Windows Communication Foundation (WCF) może być wywoływana synchronicznie lub asynchronicznie. Asynchroniczne wywołanie metody umożliwia aplikacji, aby kontynuować pracę, podczas gdy metoda jest wywoływana, gdy działa przez wolne połączenie.  
  
Domyślnie kiedy odwołania do usługi jest dodawany do projektu jest konfigurowana do wywołania metody synchronicznie. Aby zmienić zachowanie do asynchronicznego wywołania metody, zmieniając ustawienia w **odwołania do konfigurowania usługi** okno dialogowe.  
  
> [!NOTE]
>  Ta opcja jest ustawiona na podstawie-service. Gdy jedna metoda dla usługi została wywołana asynchronicznie, wszystkie metody musi zostać wywołana asynchronicznie.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>Aby wywołać metody usługi asynchronicznie  
  
1.  W **Eksploratora rozwiązań**, wybierz odwołanie do usługi.  
  
2.  Na **projektu** menu, kliknij przycisk **odwołania do konfigurowania usługi**.  
  
3.  W **odwołania do konfigurowania usługi** okno dialogowe, wybierz opcję **Generuj operacje asynchroniczne** pole wyboru.  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>Porady: powiązanie danych zwróconych przez usługę  
Można powiązać danych zwróconych przez usługę Windows Communication Foundation (WCF) do formantu tak samo jak dowolnego innego źródła danych można powiązać z formantu. Podczas dodawania odwołania do usługi WCF, jeśli usługa zawiera złożone typy, które zwracają dane, są automatycznie dodawane do **źródeł danych** okna.  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Aby powiązać formant jedno pole danych zwróconych przez usługi WCF  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**. **Źródeł danych** pojawi się okno.  
  
2.  W **źródeł danych** okna, rozwiń węzeł odwołania do usługi. Zostaną wyświetlone wszystkie typy złożone zwrócona przez usługę.  
  
3.  Rozwiń węzeł dla typu. Będą wyświetlane pola danych dla tego typu.  
  
4.  Wybierz pole i kliknij strzałkę listy rozwijanej, aby wyświetlić listę formantów, które są dostępne dla typu danych.  
  
5.  Kliknij typ formantu, który chcesz utworzyć powiązania.  
  
6.  Przeciągnij pole na formularzu. Formantu zostanie dodany do formularza razem z <xref:System.Windows.Forms.BindingSource> składnika i <xref:System.Windows.Forms.BindingNavigator> składnika.  
  
7.  Powtórz kroki 4, chociaż 6 dla żadnych innych pól, które chcesz powiązać.  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Aby powiązać formantu typu złożonego zwrócony przez usługę WCF  
  
1.  Na **danych** menu, wybierz opcję **Pokaż źródeł danych**. **Źródeł danych** pojawi się okno.  
  
2.  W **źródeł danych** okna, rozwiń węzeł odwołania do usługi. Zostaną wyświetlone wszystkie typy złożone zwrócona przez usługę.  
  
3.  Wybierz węzeł typu, a następnie kliknij strzałkę listy rozwijanej, aby wyświetlić listę dostępnych opcji.  
  
4.  Kliknij opcję **DataGridView** do wyświetlania danych w siatce lub **szczegóły** do wyświetlania danych w poszczególnych formantów.  
  
5.  Przeciągnij węzeł na formularzu. Formanty zostanie dodany do formularza razem z <xref:System.Windows.Forms.BindingSource> składnika i <xref:System.Windows.Forms.BindingNavigator> składnika.  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Porady: Konfigurowanie usługi ponowne użycie istniejących typów  
Gdy odwołania do usługi zostanie dodany do projektu, wszystkie typy zdefiniowane w usłudze są generowane w projekcie lokalnego. W wielu przypadkach, spowoduje to utworzenie zduplikowane typy gdy usługa wspólnej [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] typów lub gdy typy są definiowane w bibliotece udostępnionej.  
  
Aby uniknąć tego problemu, domyślnie są udostępniane typów w zestawach, do którego istnieje odwołanie. Jeśli chcesz wyłączyć udostępnianie dla jednego lub więcej zestawów typu, możesz to zrobić to w **skonfigurować odwołania do usług** okno dialogowe.  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Aby wyłączyć udostępnianie typu w jednym zestawie  
  
1.  W **Eksploratora rozwiązań**, wybierz odwołanie do usługi.  
  
2.  Na **projektu** menu, kliknij przycisk **odwołania do konfigurowania usługi**.  
  
3.  W **skonfigurować odwołania do usług** okno dialogowe, wybierz opcję **ponownie użyj typów w określonych przywoływanych zestawach**.  
  
4.  Zaznacz pole wyboru dla każdego zestawu, w której chcesz włączyć udostępnianie typu. Aby wyłączyć udostępnianie dla zestawu typu, pozostaw pole wyboru, wyczyszczone.  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Aby wyłączyć udostępnianie typu w wszystkie zestawy  
  
1.  W **Eksploratora rozwiązań**, wybierz odwołanie do usługi.  
  
2.  Na **projektu** menu, kliknij przycisk **odwołania do konfigurowania usługi**.  
  
3.  W **skonfigurować odwołania do usług** okno dialogowe, usuń zaznaczenie **ponownie użyj typów w przywoływanych zestawach** pole wyboru.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wskazówki: Tworzenie prostego usługi WCF w formularzach systemu Windows](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Udostępnia krok Pokaz tworzenia i używania usługi WCF w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Wskazówki: Tworzenie usługi danych WCF z WPF i strukturą Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Udostępnia pokaz krok po kroku dotyczące tworzenia i używania [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Używanie narzędzi deweloperskich programu WCF](/dotnet/framework/wcf/using-the-wcf-development-tools)|W tym artykule omówiono sposób tworzenia i testowania usługi WCF w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
||[Porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Omówiono sposób odwołania i użyj [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md)|Przedstawia informacje o niektórych typowych błędów, które mogą wystąpić z odwołania do usług i jak zapobiec ich.|  
|[Debugowanie usług WCF](../debugger/debugging-wcf-services.md)|W tym artykule opisano typowe problemy debugowania i techniki, które mogą wystąpić podczas debugowania usług WCF.|  
|[Wskazówki: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Zawiera szczegółowe instrukcje dotyczące tworzenie typizowanego zestaw danych i rozdzielić wiele projektów kodu TableAdapter i zestawu danych.|  
|[Konfiguruj odwołanie do usługi — okno dialogowe](../data-tools/configure-service-reference-dialog-box.md)|W tym artykule opisano elementy interfejsu użytkownika z **odwołania do konfigurowania usługi** okno dialogowe.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)