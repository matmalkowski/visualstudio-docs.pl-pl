---
title: "Wdrażanie składników COM za pomocą technologii ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a63073e86c3584253e67bf4d77f43006104de075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-com-components-with-clickonce"></a>Wdrażanie składników COM za pomocą technologii ClickOnce
Wdrożenie starszych składników modelu COM został tradycyjnie trudne. Składniki należy zarejestrować globalnie i w związku z tym może spowodować niepożądane skutki uboczne między aplikacjami nakładające się. Ta sytuacja zwykle nie jest problem w aplikacjach .NET Framework, ponieważ składniki są całkowicie odizolowane do aplikacji lub side-by-side zgodny. Program Visual Studio umożliwia wdrażanie izolowane składniki modelu COM systemu Windows XP lub wyższej systemu operacyjnego.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]udostępnia mechanizm łatwego i bezpiecznego wdrażania aplikacji platformy .NET. Jednak aplikacje użyć starszego składniki modelu COM, należy wykonać dodatkowe kroki w celu ich wdrożenia. W tym temacie opisano sposób wdrażania izolowane składniki COM i odwołać natywnego składników (na przykład z programu Visual Basic 6.0 lub Visual C++).  
  
 Aby uzyskać więcej informacji na temat izolowane składniki COM wdrażania, zobacz "Uprość wdrożenia aplikacji z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i COM bez rejestrowania" w [http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM bez rejestrowania  
 COM bez rejestrowania jest to nowa technologia, wdrażania i aktywowanie izolowane składniki COM. Działa on umieszczenie biblioteki typów wszystkich składników i informacji o rejestracji, który zazwyczaj jest zainstalowany w rejestrze systemu do pliku XML manifestu, nazywany przechowywane w tym samym folderze co aplikacja.  
  
 Izolowanie składnika modelu COM wymaga on być zarejestrowany na komputerze dewelopera, ale nie musi być zarejestrowana na komputerze użytkownika końcowego. Aby wyizolować składnika modelu COM, należy wykonać jest gotowe jego odwołania **izolowany** właściwości **True**. Domyślnie, ta właściwość jest ustawiona wartość **False**, wskazujący, że powinny być traktowane jako odwołanie COM w zarejestrowany. Jeśli ta właściwość jest **True**, spowoduje wygenerowanie manifestu ma zostać wygenerowane przez ten składnik w czasie kompilacji. Powoduje także odpowiadające im pliki mają być kopiowane do folderu aplikacji podczas instalacji.  
  
 Gdy manifestu generator napotka izolowanego odwołania COM, wylicza wszystkie `CoClass` wpisów w bibliotece typów składnika dopasowywania każdego wpisu z jej odpowiednie dane rejestracji i generowania manifestu definicje dla modelu COM klasy w pliku biblioteki typów.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Wdrażanie składników COM bez rejestrowania za pomocą aplikacji ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]technologii wdrażania jest dobrze nadaje się do wdrażania izolowane składniki modelu COM, ponieważ zarówno [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i COM bez rejestrowania wymagają, aby składnik miał manifest, aby można było wdrożyć.  
  
 Zazwyczaj autora składnika powinien zapewnić manifestu. Jeśli nie, jednak może generować automatycznie manifestu składnika modelu COM jest Visual Studio. Generowanie manifestu jest wykonywane podczas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proces publikowania; Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md). Ta funkcja pozwala również na lepsze wykorzystanie starszych składników, które utworzone w starszej środowiskach programistycznych, takich jak Visual Basic 6.0.  
  
 Istnieją dwa sposoby który [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdraża składniki COM:  
  
-   Użyj inicjujący, aby wdrożyć składniki modelu COM; to działanie na wszystkich obsługiwanych platformach.  
  
-   Użyj składnik macierzysty wdrożenie izolacji (znanej także jako COM bez rejestrowania). Jednak działa tylko na Windows XP lub wyższej systemu operacyjnego.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Przykład izolowanie i wdrażania prostego składnika modelu COM  
 W celu zaprezentowania wdrożenie składnika COM bez rejestrowania, w tym przykładzie zostanie tworzenie aplikacji systemu Windows w języku Visual Basic, odwołujący się izolowanego natywnego składnika COM utworzone za pomocą Visual Basic 6.0 i wdróż je za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Najpierw należy utworzyć natywnej składnika modelu COM:  
  
##### <a name="to-create-a-native-com-component"></a>Aby utworzyć natywnej składnika modelu COM  
  
1.  Za pomocą Visual Basic 6.0 z **pliku** menu, kliknij przycisk **nowy**, następnie **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **Visual Basic** a następnie wybierz węzeł **ActiveX DLL** projektu. W **nazwa** wpisz `VB6Hello`.  
  
    > [!NOTE]
    >  Obsługiwane są tylko typy projektu ActiveX DLL i kontrolki ActiveX z COM bez rejestrowania; Typy projektów ActiveX EXE i zarządzania dokumentami ActiveX nie są obsługiwane.  
  
3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Class1.vb** można otworzyć edytora tekstu.  
  
4.  W Class1.vb, Dodaj następujący kod po wygenerowany kod dla `New` metody:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Tworzenie składnika. Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
> [!NOTE]
>  COM bez rejestrowania obsługuje tylko biblioteki dll i COM kontroluje typów projektów. Nie można używać plików exe bez rejestrowania modelu COM.  
  
 Można teraz tworzenie aplikacji systemu Windows i Dodaj odwołanie do składnika COM do niej.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Do tworzenia aplikacji opartych na systemie Windows za pomocą składnika modelu COM  
  
1.  Za pomocą języka Visual Basic z **pliku** menu, kliknij przycisk **nowy**, następnie **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **Visual Basic** a następnie wybierz węzeł **aplikacji systemu Windows**. W **nazwa** wpisz `RegFreeComDemo`.  
  
3.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisk, aby wyświetlić odwołania do projektu.  
  
4.  Kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie** z menu kontekstowego.  
  
5.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **Przeglądaj** , przejdź do VB6Hello.dll, a następnie wybierz go.  
  
     A **VB6Hello** odwołanie, znajduje się na liście odwołań.  
  
6.  Wskaż **przybornika**, wybierz pozycję **przycisk** kontroli, a następnie przeciągnij ją do **Form1** formularza.  
  
7.  W **właściwości** Ustaw przycisku **tekst** właściwości **Hello**.  
  
8.  Kliknij dwukrotnie przycisk, aby dodać kod obsługi, a w pliku kodu, Dodaj kod, tak aby program obsługi o następującej treści:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Uruchom aplikację. Z **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
 Następnie wymagany do izolowania formantu. Każdy składnik COM, który korzysta z aplikacji jest reprezentowana w projektu jako odwołania COM. Te odwołania są widoczne w obszarze **odwołania** w węźle **Eksploratora rozwiązań** okna. (Zwróć uwagę, że można dodawać odwołuje się bezpośrednio przy użyciu **Dodaj odwołanie** na **projektu** menu lub pośrednio, przeciągając formantu ActiveX na formularzu.)  
  
 Poniższe kroki pokazują, jak izolować składnika modelu COM i publikowanie aplikacji zaktualizowane zawierająca formant izolowanym:  
  
##### <a name="to-isolate-a-com-component"></a>Aby odizolować składnika modelu COM  
  
1.  W **Eksploratora rozwiązań**w **odwołania** węzła, wybierz opcję **VB6Hello** odwołania.  
  
2.  W **właściwości** okna, zmień wartość **izolowany** właściwość z **False** do **True**.  
  
3.  Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
 Teraz, gdy zostanie naciśnięty klawisz F5, aplikacja działa zgodnie z oczekiwaniami, ale jest teraz uruchomiona w obszarze bez rejestrowania modelu COM. W celu potwierdzenia, spróbuj wyrejestrowywania składnika VB6Hello.dll i uruchomić RegFreeComDemo1.exe poza środowiska IDE programu Visual Studio. Teraz po kliknięciu przycisku nadal działa. Jeśli zmienisz tymczasowo manifest aplikacji, ponownie powiedzie.  
  
> [!NOTE]
>  Brak składnika modelu COM można symulować tymczasowo wyrejestrowując go. Otwórz wiersz polecenia, przejdź do folderu systemu, wpisując `cd /d %windir%\system32`, następnie wyrejestrować składnika, wpisując `regsvr32 /u VB6Hello.dll`. Zarejestruj je ponownie, wpisując `regsvr32 VB6Hello.dll`.  
  
 Ostatnim krokiem jest opublikowanie aplikacji przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Publikowanie aplikacji przy użyciu izolowanego składnika modelu COM  
  
1.  Z **kompilacji** menu, kliknij przycisk **publikowania RegFreeComDemo**.  
  
     Zostanie wyświetlony Kreator publikowania.  
  
2.  W Kreatorze publikowanie Określ lokalizację na dysku na komputerze lokalnym, gdzie można uzyskać dostęp i sprawdź, czy plików publikowanych.  
  
3.  Kliknij przycisk **Zakończ** do publikowania aplikacji.  
  
 Podczas badania plików publikowanych, można zauważyć, że plik sysmon.ocx jest dołączony. Formant jest całkowicie izolowane dla tej aplikacji, co oznacza, że komputerze użytkownika końcowego jest inna aplikacja używa innej wersji formantu, nie może przeszkadzać do za pomocą tej aplikacji.  
  
## <a name="referencing-native-assemblies"></a>Natywny zestawy odwołujące  
 Program Visual Studio obsługuje odwołań do natywnej Visual Basic 6.0 lub zestawy C++; takie odwołania są nazywane odwołaniami macierzystego. Można sprawdzić, czy odwołanie jest natywny, upewniając się, że jego **typ pliku** właściwość jest ustawiona na **natywnego** lub **ActiveX**.  
  
 Aby dodać odwołanie do natywnego, użyj **Dodaj odwołanie** polecenia, a następnie przejdź do manifestu. Niektóre składniki umieść manifestu w bibliotece DLL. W takim przypadku można po prostu wybierz plik DLL, który sam i Visual Studio zostanie dodane jako odwołanie do natywnego, jeśli wykryje, że składnik zawiera osadzony manifestu. Visual Studio będzie automatycznie dołączać pliki zależne i zestawy wymienione w manifeście, jeśli są w tym samym folderze, do którego istnieje odwołanie składnika.  
  
 Izolacja kontrolki COM ułatwia wdrażanie składników COM, które nie mają jeszcze manifestów. Jednak jeśli składnik jest dostarczany z manifestu, możesz bezpośrednio odwoływać manifestu. W rzeczywistości należy zawsze używać manifestu dostarczonych przez autora składnika, tam gdzie to możliwe, zamiast używania **izolowany** właściwości.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Ograniczenia dotyczące wdrażania składnika modelu COM bez rejestrowania  
 COM bez rejestrowania zalety wyczyść przez techniki tradycyjnego wdrażania. Jednak istnieje kilka ograniczeń i uwagi, które należy również wskazać. Największe ograniczenie jest, że działa ona tylko w systemie Windows XP lub nowszego. Implementacja COM bez rejestrowania wymagane zmiany ładowania składników w podstawowego systemu operacyjnego. Niestety nie jest nie warstwę obsługi niskiego poziomu dla bez rejestrowania modelu COM.  
  
 Nie każdy składnik jest odpowiedni kandydatem do bez rejestrowania modelu COM. Składnik nie jest odpowiedni, jeśli spełnione są następujące:  
  
-   Składnik jest serwerem poza procesem. Serwery EXE nie są obsługiwane; obsługiwane są tylko biblioteki dll.  
  
-   Składnik jest częścią systemu operacyjnego lub jest składnikiem systemu, takie jak XML, program Internet Explorer lub Microsoft Data Access Components (MDAC). Należy stosować zasady redystrybucji autora składników; Skontaktuj się z dostawcą.  
  
-   Składnik jest częścią aplikacji, takich jak Microsoft Office. Na przykład nie powinny podejmować izolować modelu obiektów programu Microsoft Excel. To jest częścią pakietu Office i można używać tylko na komputerze z zainstalować produkt w pełnym pakietu Office.  
  
-   Składnik jest przeznaczony do użycia jako dodatek lub przystawki, na przykład dodatków pakietu Office lub formantu w przeglądarce sieci Web. Takie składniki zwykle wymagają określonego rodzaju schemat rejestracji zdefiniowany przez środowisko hostingu wykracza poza zakres manifestu samej siebie.  
  
-   Składnik zarządza urządzenia fizyczne lub wirtualne dla systemu, na przykład sterownika urządzenia dla buforu wydruku.  
  
-   Składnik jest dostęp do danych do dystrybucji. Dane aplikacji wymagają oddzielnego dostępu do danych pakietu redystrybucyjnego do zainstalowania przed uruchomieniem. Nie należy próbować izolować składniki, takie jak kontrolka danych ADO firmy Microsoft, Microsoft OLE DB lub Microsoft Data Access Components (MDAC). Zamiast tego Jeśli aplikacja korzysta z programu MDAC lub SQL Server Express, należy ustawić je jako wymagania wstępne; zobacz [porady: instalowanie wstępnie wymaganych składników w aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 W niektórych przypadkach może być możliwe w dla deweloperów składnika zmodyfikowanie go dla bez rejestrowania modelu COM. Jeśli nie jest to możliwe, można nadal kompilacji i publikowania aplikacji, które zależą od nich za pośrednictwem schemat standardowe rejestracji przy użyciu inicjujący. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
 Składnik COM może być tylko raz izolowanym, według aplikacji. Na przykład nie można odizolować tego samego składnika modelu COM z dwóch różnych **biblioteki klas** projektów, które są częścią tej samej aplikacji. Spowoduje to ostrzeżenie kompilacji, a aplikacja będzie można załadować w czasie wykonywania. Aby uniknąć tego problemu, firma Microsoft zaleca, aby hermetyzować składniki modelu COM w bibliotece jednej klasy.  
  
 Istnieje kilka scenariuszy, w których COM jest wymagana rejestracja na komputerze dewelopera, mimo że wdrożenie aplikacji nie wymaga rejestracji. `Isolated` Właściwość wymaga można zarejestrować składnika COM na komputerze dewelopera w celu automatycznego generowania manifestu podczas kompilacji. Nie ma żadnych Przechwytywanie rejestracji możliwości, które wywołują rejestrację automatyczną, podczas kompilacji. Ponadto wszystkie klasy nie jest jawnie zdefiniowany w bibliotece typów nie zostaną odzwierciedlone w manifeście. Podczas używania składnika modelu COM z istniejącym manifestu, takich jak natywne odwołanie, składnik nie może być konieczne można zarejestrować w czasie opracowywania. Jednak rejestracji jest wymagany, jeśli składnik jest formantu ActiveX, i chcesz uwzględnić w **przybornika** i Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)