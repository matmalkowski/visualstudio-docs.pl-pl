---
title: "Wskazówki: Tworzenie usługi języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 256a609dad857097731e4914a11623fe62ad7664
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Wskazówki: Tworzenie usługi języka starsza wersja
Używanie klas języka framework (MPF) zarządzanego pakietu do wdrożenia usługi języka [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jest prosta. Należy pakiet VSPackage do obsługi usługi języka, samej usługi języka i analizatora dla danego języka.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablon projektu pakietu Visual Studio  
 Szablon projektu pakietu Visual Studio można znaleźć w trzech miejscach innego szablonu w **nowy projekt** okno dialogowe:  
  
1.  W obszarze rozszerzalności języka Visual Basic. Domyślny język projektu jest Visual Basic.  
  
2.  W języku C# rozszerzalności. Domyślny język projektu jest C#.  
  
3.  W obszarze innych rozszerzeń typy projektu. Domyślny język projektu jest C++.  
  
### <a name="create-a-vspackage"></a>Utwórz pakiet VSPackage  
  
1.  Utwórz nowy pakiet VSPackage z szablonem projektu pakietu Visual Studio.  
  
     Jeśli dodajesz usługi języka Aby istniejący pakiet VSPackage, pominęli następujące kroki i przejść bezpośrednio do procedury "Tworzenie języka klasy usługi".  
  
2.  Wprowadź nazwę projektu MyLanguagePackage i kliknij przycisk **OK**.  
  
     Można użyć dowolnego nazwę. Te procedury opisane w tym miejscu założono MyLanguagePackage jako nazwy.  
  
3.  Wybierz [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jako język i opcję, aby wygenerować nowy plik klucza. Kliknij przycisk **Dalej**.  
  
4.  Wprowadź odpowiednie informacje firmy i pakietu. Kliknij przycisk **Dalej**.  
  
5.  Wybierz **polecenie**. Kliknij przycisk **Dalej**.  
  
     Jeśli nie zamierzasz obsługuje wstawki kodu, można po prostu kliknij przycisk Zakończ i pomiń następny krok.  
  
6.  Wprowadź **wstawianie fragmentu kodu** jako **polecenia nazwa** i `cmdidInsertSnippet` dla **identyfikator polecenia**. Kliknij przycisk **Zakończ**.  
  
     **Nazwa polecenia** i **identyfikator polecenia** może być dowolne, po prostu przykłady.  
  
### <a name="create-the-language-service-class"></a>Tworzenie klasy usługi języka  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy na projekt MyLanguagePackage, wybierz polecenie **Dodaj**, **odwołania**, a następnie wybierz pozycję **Dodaj nowe odwołanie** przycisku.  
  
2.  W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualStudio.Package.LanguageService** w **.NET** i kliknij polecenie **OK**.  
  
     Musi to być przeprowadzane tylko raz dla projektu pakietu języka.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy pakiet VSPackage projektu i wybierz **Dodaj**, **klasy**.  
  
4.  Upewnij się, że **klasy** jest zaznaczony na liście szablonów.  
  
5.  Wprowadź **MyLanguageService.cs** nazwę pliku klasy i kliknij przycisk **Dodaj**.  
  
     Można użyć dowolnego nazwę. Te procedury opisane w tym miejscu założono `MyLanguageService` jako nazwy.  
  
6.  W pliku MyLanguageService.cs, Dodaj następujący `using` instrukcje.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modyfikowanie `MyLanguageService` pochodzi od klasy <xref:Microsoft.VisualStudio.Package.LanguageService> klasy:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Umieść kursor na "LanguageService" i z **Edytuj**, **IntelliSense** menu, wybierz opcję **implementacji klasy abstrakcyjnej**. Spowoduje to dodanie minimalne wymagane metody służące do implementacji klasy usługi języka.  
  
9. Implementuje metody abstrakcyjne zgodnie z opisem w [implementacja usługi języka starszych](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Zarejestruj usługę języka  
  
1.  Otwórz plik MyLanguagePackagePackage.cs i dodaj następujące `using` instrukcji:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Zarejestruj klasie usługi języka, zgodnie z opisem w [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md). W tym ProvideXX atrybutów i sekcji "Proffering usługi języka". Użyj MyLanguageService, których używa TestLanguageService w tym temacie.  
  
### <a name="the-parser-and-scanner"></a>Analizator i skanera  
  
1.  Implementowanie analizatora i skanera dla danego języka, zgodnie z opisem w [analizatora usługi języka starszych i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Jak zaimplementować analizatora, a skanera całkowicie zależy i wykracza poza zakres tego tematu.  
  
## <a name="language-service-features"></a>Funkcje usługi języka  
 Do każdej funkcji należy zaimplementować w usłudze języka, należy zwykle pochodzi od odpowiedniej klasy usługi języka MPF klasy, wdrożenia dowolnej metody abstrakcyjne odpowiednio do potrzeb i zastąpić odpowiedniej metody. Jakie klasy utworzenia i/lub pochodzić od jest zależna od funkcji planowane obsługuje. Funkcje te omówiono szczegółowo w [funkcji usługi języka starszych](../../extensibility/internals/legacy-language-service-features1.md). Poniższa procedura jest ogólne podejście wyprowadzanie z klas MPF klasy.  
  
#### <a name="deriving-from-an-mpf-class"></a>Wyprowadzanie z klas MPF  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy pakiet VSPackage projektu i wybierz **Dodaj**, **klasy**.  
  
2.  Upewnij się, że **klasy** jest zaznaczony na liście szablonów.  
  
     Wprowadź odpowiednią nazwę klasy, a następnie kliknij przycisk **Dodaj**.  
  
3.  W nowym pliku klasy, Dodaj następujący `using` instrukcje.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modyfikowanie klasy pochodzić z odpowiednią klasę MPF.  
  
5.  Dodaj Konstruktor klasy, który ma co najmniej takich samych parametrach co konstruktor klasy podstawowej i przekazania parametrów konstruktora do konstruktora klasy podstawowej.  
  
     Na przykład konstruktora dla klasy pochodzące z <xref:Microsoft.VisualStudio.Package.Source> klasy może wyglądać następująco:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Z **Edytuj**, **IntelliSense** menu, wybierz opcję **implementacji klasy abstrakcyjnej** Jeśli klasa podstawowa ma wszystkie metody abstrakcyjne, które muszą zostać zaimplementowane.  
  
7.  W przeciwnym razie pozycji karetki wewnątrz klasy i wprowadź metody do zastąpienia.  
  
     Na przykład wpisz `public override` umożliwia wyświetlenie listy wszystkich metod, które mogą zostać zastąpione przez tę klasę.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service1.md)