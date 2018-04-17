---
title: Visual Studio Emulator for Android | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55e1e24a1482f40664d3f0c154d362c08bb9fa17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-emulator-for-android"></a>Emulator programu Visual Studio dla systemu Android
Visual Studio Emulator for Android to aplikacja komputerowa, która emuluje urządzenie z systemem Android. Umożliwia środowisku wirtualnym, w którym można debugowania i testowania aplikacji systemu Android bez urządzenia fizycznego. Umożliwia także izolowane środowisko prototypów aplikacji.  

> [!IMPORTANT]
> W większości przypadków emulator systemu Google Android jest zalecane używanie zamiast programu Visual Studio Emulator for Android:
> - Jeśli jesteś w musi zawierający systemu Android w wersji 7.0 lub nowszej, ponieważ nie ma żadnych planów publikowania Android — obrazy emulatora obrazy poza do użycia w programie Visual Studio Emulator for Android w wersji 6.0.
> - Przy użyciu programu Visual Studio Tools for Apache Cordova. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji platformy Apache Cordova w systemie Android](/visualstudio/cross-platform/tools-for-cordova/run-your-app/run-app-android#a-idgoogle-android-emulatora-run-on-the-google-android-emulator).
  
 Visual Studio Emulator for Android zaprojektowano w celu zapewnienia można porównywać pod względem wydajności do rzeczywistego urządzenia. Przed opublikowaniem aplikacji, jednak zaleca się przetestowanie aplikacji na urządzeniu fizycznym.  
  
 Można przetestować aplikację na profilu unikatowych urządzeń dla każdej platformy systemu Android, rozdzielczości ekranu i innych właściwości sprzętu obsługiwana w programie Visual Studio Emulator for Android.
  
##  <a name="Installing"></a> Instalowanie i odinstalowywanie  
 Instalowanie programu  
  
 Visual Studio Emulator for Android to składnik wieloplatformowych narzędzi dostępnych w programie Visual Studio i zostanie zainstalowany podczas niestandardowej instalacji programu Visual Studio po wybraniu wieloplatformowych aplikacji mobilnych, a następnie popularne narzędzia i zestawy Software Development Kit a następnie w programie Visual Studio Emulator for Android.  
  
 Odinstalowanie  
  
 Musisz odinstalować emulatora programu Visual Studio dla systemu Android przy użyciu apletu Dodaj/Usuń programy w Panelu sterowania.  
  
> [!NOTE]
>  Odinstalowanie programu Visual Studio nie spowoduje odinstalowania emulator. Należy odinstalować emulator oddzielnie.  
  
 Po odinstalowaniu programu Visual Studio Emulator for Android funkcji Hyper-V wirtualne Ethernet karty sieciowe utworzone dla emulator używany nie są automatycznie usuwane. Można ręcznie usunąć te wirtualne karty sieciowe (jeśli jest nieużywany), otwórz Menedżera funkcji Hyper-V, wybierając jedną z obrazami VHD emulatora, wybierając kartę sieci i wybierając pozycję **Usuń** dla wszystkich przełączników, które pojawia się na tej karcie.  
  
##  <a name="Requirements"></a> Wymagania systemowe i zgodności z poprzednimi wersjami  
 Ważne informacje o sprzętu, oprogramowania i wymagania dotyczące konfiguracji dla programu Visual Studio Emulator for Android zobacz następujący temat.  
  
-   [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Visual Studio Emulator for Android wymaga programu Visual Studio 2015 roku. nie są zgodne ze starszymi wersjami programu Visual Studio.  
  
 Nowe wersje emulatora są instalowane na starsze wersje (i w niektórych przypadkach mogą zastąpić starego obrazów, odrzucając ustawień, aplikacji i plików instalowanych w tych obrazów).  
  
##  <a name="Networking"></a> Obsługa sieci w programie Visual Studio Emulator for Android  
 Sieciowe połączenie emulatora programu Visual Studio dla systemu Android zachowuje się jak połączenie komputera stacjonarnego z tę charakterystykę:  
  
-   Emulator pojawia się w sieci jako osobne urządzenia z adresu IP.  
  
-   Nie jest wymagane dodatkowe oprogramowanie sieciowe, który nie jest już zainstalowany w emulatorze.  
  
-   Nie jest przyłączony do domeny systemu Windows.  
  
 Aby poznać możliwości połączenia sieciowego emulatora, go traktować jako podobne do połączenia sieci Wi-Fi na telefonie z systemem Android do tej samej sieci. Jeśli aplikacji uruchomionej na Twój telefon można uzyskać dostęp do zasobów sieciowych za pośrednictwem połączenia sieci Wi-Fi, w aplikacji uruchomionej na emulatorze można również dostęp do tego samego zasobu sieciowego.  
  
 Aby uzyskać więcej informacji na wymagania dotyczące sieci, zobacz [wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Aby uzyskać informacje na temat rozwiązywania problemów z sieci, zobacz [Rozwiązywanie problemów z programu Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Configuring"></a> Konfigurowanie programu Visual Studio Emulator for Android  
 Testowanie aplikacji systemu Android dla zgodności między różnicowanie różnych Android sprzętu może być wyzwaniem. Telefony i tablety na rynku obejmują szeroki zakres wersji i rozmiaru ekranu i są dostępne w wielu różnych konfiguracji sprzętu (RAM, procesory, architektura itp.). Visual Studio Emulator for Android upraszcza to przy użyciu profilów urządzeń. Nasze zbiór profilów urządzeń reprezentują najpopularniejszych sprzętu na rynku, w tym urządzeń Samsung, firmie, Sony i LG.  
  
 W programie Visual Studio 2015 można zainstalować, odinstalować i uruchomić profilów urządzeń za pomocą Menedżera emulatora. Dostęp do Menedżera emulatora, wybierając **narzędzia**, następnie **programu Visual Studio Emulator for Android**.  
  
 ![Emulator programu Visual Studio dla systemu Android Menedżera](../cross-platform/media/android_emu_manager.png "Android_Emu_Manager")  
  
 Domyślnie są cztery profile wstępnie zainstalowane urządzenie (KitKat i interfejs typu lizak phone/5 "i tablet/7" konfiguracje), wskazywany przez białego tekstu i ikon. Innych profilów na liście będą wyszarzone dopóki nie wybierzesz **Instalowanie profilu** zakończeniu przycisk i instalacji. Można filtrować na liście według poziom interfejsu API i kliknij strzałkę szczegółów w prawym dolnym rogu profilu, aby wyświetlić jego szczegóły pełnej konfiguracji.  
  
 Po zainstalowaniu zbiór profilów, które ma zostać celem tych nowych profilów można uruchomić bezpośrednio z Menedżera naciskając zielonego **odtwarzanie** przycisku. Zostanie również pojawią się one w menu rozwijanym docelowego debugowania w typu i platform przenośnych projektu programu Visual Studio.  
  
##  <a name="FeaturesTest"></a> Funkcje, które można sprawdzić w emulatorze  
 Aby uzyskać szczegółowe informacje na temat funkcji, można sprawdzić w emulatorze, zobacz ten [wpis w blogu](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
##  <a name="FeaturesNonTest"></a> Funkcje, których nie można sprawdzić w emulatorze  
 Poniższa lista zawiera funkcje platformy systemu Android że **nie** testu w emulatorze. Należy przetestować te funkcje na urządzeniu fizycznym.  
  
-   Kompas  
  
-   Żyroskop  
  
-   Kontroler wibrację  
  
-   Jasność. Zmiana poziomu jasności emulatora będzie nie wizualnie wpływu na sposób wyświetlania na ekranie urządzenia.  
  
##  <a name="Support"></a> Zasoby pomocy technicznej  
 Jeśli komputer-host spełnia wymagania systemowe i nie wystąpi problem omówione w tym przewodniku rozwiązywania problemów:  
  
-   Zadaj pytanie na temat używania StackOverflow [emulatora systemu android](http://stackoverflow.com/questions/tagged/android-emulator) i znacznika visual studio.  
  
-   Zgłoś problem za pomocą Wyślij uśmiech narzędzia programu Visual Studio lub w Menedżerze emulatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
