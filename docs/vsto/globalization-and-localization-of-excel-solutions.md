---
title: "Lokalizacja i globalizacja rozwiązań w programie Excel | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: globalization [Office development in Visual Studio], configuring
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 66c997dd8de6801d790b7653ca414cac0996ddc9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Lokalizacja i globalizacja rozwiązań programu Excel
  Ta sekcja zawiera informacje o uwagi dotyczące rozwiązania programu Microsoft Office Excel, które będą uruchamiane na komputerach z systemem innym niż angielski ustawienia dla systemu Windows. Większością aspektów globalizacja i lokalizacja pakietu Microsoft Office są takie same, jak podczas tworzenia innych rodzajów rozwiązań za pomocą programu Visual Studio. Aby uzyskać ogólne informacje, zobacz [Globalizing i lokalizacja aplikacji](/visualstudio/ide/globalizing-and-localizing-applications).  
  
 Domyślnie formanty hosta w oprogramowaniu Microsoft Office Excel prawidłowo w przypadku każdego ustawienia regionalne systemu Windows tak długo, jak wszystkie dane, które są przekazywane lub modyfikować za pomocą kodu zarządzanego jest sformatowany przy użyciu formatowania język angielski (Stany Zjednoczone). W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], to zachowanie jest kontrolowany przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="formatting-data-in-excel-with-various-regional-settings"></a>Formatowanie danych w programie Excel przy użyciu różnych ustawień regionalnych  
 Należy sformatować wszystkie dane, które są zależne od ustawień regionalnych formatowanie, takich jak daty i walut, przy użyciu formatu danych angielski (Stany Zjednoczone) (1033 identyfikator ustawień regionalnych) przed przekaż go do programu Microsoft Office Excel lub odczytać danych z kodu projektu pakietu Office.  
  
 Domyślnie podczas opracowywania rozwiązań pakietu Office w Visual Studio modelu obiektów programu Excel oczekuje formatowania danych 1033 identyfikator ustawień regionalnych (jest to również nazywane blokowania modelu obiektowego 1033 identyfikator ustawień regionalnych). To zachowanie jest zgodny sposób, w jaki Visual Basic for Applications działa. Jednak to zachowanie można zmienić w ramach rozwiązań pakietu Office.  
  
### <a name="understanding-how-the-excel-object-model-always-expects-locale-id-1033"></a>Zrozumienie, jak Model obiektów programu Excel zawsze oczekuje identyfikator ustawień regionalnych 1033  
 Domyślnie rozwiązań pakietu Office, które utworzono za pomocą programu Visual Studio są niezależne od ustawień regionalnych użytkownika końcowego i zawsze zachowują się tak, jakby ustawień regionalnych jest angielski (Stany Zjednoczone). Na przykład get lub set <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> właściwości w programie Excel, dane muszą być sformatowane w sposób, który oczekuje identyfikator ustawień regionalnych 1033. Jeśli używasz formatu danych, może uzyskać nieoczekiwane wyniki.  
  
 Mimo że używasz formatu angielski (Stany Zjednoczone) dla danych przekazany lub modyfikowany w zakresie przez kod zarządzany, Excel interpretuje i wyświetla dane poprawnie w zależności od ustawień regionalnych użytkownika końcowego. Excel można sformatować dane poprawnie, ponieważ kod zarządzany przekazuje format 1033 identyfikator ustawień regionalnych wraz z danymi, co oznacza, że dane są w języku angielskim (Stany Zjednoczone) i musi być sformatowany do dopasowania ustawień regionalnych użytkownika.  
  
 Na przykład, jeśli użytkownicy końcowi ich opcje regionalne, ustawienia regionalne niemiecki (Niemcy), oczekiwane data 29 czerwca 2005 formatowania w ten sposób: 29.06.2005. Jednak jeśli rozwiązanie przekazuje daty do programu Excel w postaci ciągu, należy sformatować datę ustawioną w formacie angielski (Stany Zjednoczone): 2005-6/29. Jeśli komórka jest w formacie daty komórki, Excel wyświetli datę w formacie niemiecki (Niemcy).  
  
### <a name="passing-other-locale-ids-to-the-excel-object-model"></a>Przekazywanie innych identyfikatorów ustawień regionalnych w modelu obiektów programu Excel  
 Środowisko uruchomieniowe języka wspólnego (CLR) przekazuje automatycznie 1033 identyfikator ustawień regionalnych wszystkie metody i właściwości w modelu obiektów programu Excel, które akceptują danych zależne od ustawień regionalnych. Nie istnieje sposób zmienić to zachowanie automatycznie dla wszystkich wywołań object model. Jednak można przekazać identyfikator ustawień regionalnych różnych do określonej metody przy użyciu <xref:System.Type.InvokeMember%2A> do wywoływania metody i przekazując identyfikator ustawień regionalnych *kultury* parametru metody.  
  
## <a name="localizing-document-text"></a>Lokalizowanie tekst dokumentu  
 Dokument, szablon lub skoroszyt w projekcie prawdopodobnie zawiera statyczny tekst, który musi być zarządzane zasoby zlokalizowane oddzielnie z zestawu i innych. Łatwe w tym celu jest kopię dokumentu i tłumaczenie tekstu przy użyciu programu Microsoft Office Word i Microsoft Office Excel. Ten proces działa nawet w przypadku braku zmian w kodzie, ponieważ dowolną liczbę dokumentów może odnosić się do tego samego zestawu.  
  
 Nadal należy się upewnić, że dowolną część swój kod, który współdziała z tekstem dokumentu w dalszym ciągu język tekstu i tej zakładki o nazwie zakresów, i innych polach pomieścić formatowania dokumentu pakietu Office, które było konieczne dostosowywać różne długości gramatyki i tekst. Szablony dokumentów zawierających stosunkowo mały tekst można wziąć pod uwagę przechowywanie tekstu w plikach zasobów, a następnie ładowania tekst w czasie wykonywania.  
  
### <a name="text-direction"></a>Kierunek tekstu  
 W programie Excel można ustawić właściwości arkusza do renderowania tekstu od prawej do lewej. Host kontrolek ani żadnego formantu, który ma `RightToLeft` właściwości, które są automatycznie umieszczane w Projektancie odpowiada te ustawienia w czasie wykonywania. Program Word nie ma ustawienia dokumentu dla tekstu dwukierunkowego (można zmienić wyrównania tekstu w sieci), więc formantów nie można zamapować na to ustawienie. Zamiast tego należy ustawić wyrównania tekstu dla każdego formantu. Istnieje możliwość napisz kod umożliwiający przeprowadzenie wszystkie formanty i wymusić renderowanie tekstu od prawej do lewej.  
  
### <a name="changing-culture"></a>Zmiana kultury  
 Kod dostosowania na poziomie dokumentu zazwyczaj udostępnia głównego wątku interfejsu użytkownika programu Excel, więc wszelkie zmiany wprowadzone do kultury wątku ma wpływ na wszystkich innych urządzeń, który działa na tym wątku; zmiany nie jest ograniczone do dostosowanie.  
  
 Formanty formularzy systemu Windows są inicjowane przed dodatkach na poziomie aplikacji VSTO są uruchamiane przez aplikację hosta. W takich sytuacjach należy zmienić kultura przed ustawieniem kontrolek interfejsu użytkownika.  
  
## <a name="installing-the-language-packs"></a>Instalowanie pakietów językowych  
 Jeśli ustawienia innej niż angielska dla systemu Windows, można zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pakietów językowych, aby wyświetlić [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wiadomości w języku systemu Windows. Jeśli wszyscy użytkownicy końcowi uruchomić rozwiązań z ustawieniami innej niż angielska dla systemu Windows, muszą one mieć pakiet językowy poprawne, aby wyświetlać komunikaty środowiska uruchomieniowego w języku systemu Windows. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Pakiety językowe są dostępne z [Microsoft Download Center](http://www.microsoft.com/downloads).  
  
 Ponadto do dystrybucji pakietów językowych programu .NET Framework są niezbędne dla komunikatów ClickOnce. Pakiety językowe programu .NET Framework są dostępne z [Microsoft Download Center](http://www.microsoft.com/downloads).  
  
## <a name="regional-settings-and-excel-com-calls"></a>Ustawienia regionalne i wywołania programu Excel COM  
 Zawsze, gdy klient zarządzany wywołuje metodę dla obiekt COM i należy go przekazać informacje specyficzne dla kultury, tak więc przy użyciu <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (ustawienia regionalne), które odpowiadają bieżącym ustawienia regionalne wątku. Bieżące ustawienia regionalne wątku jest dziedziczona z ustawień regionalnych użytkownika domyślnie. Jednak gdy wywołanie modelu obiektów programu Excel z rozwiązania programu Excel utworzony za pomocą narzędzi programowania pakietu Office w Visual Studio, format danych angielski (Stany Zjednoczone) (1033 identyfikator ustawień regionalnych) są przekazywane do modelu obiektów programu Excel automatycznie. Wszystkie dane, które są zależne od ustawień regionalnych formatowanie, takich jak daty i walut, należy sformatować przy użyciu formatu danych angielski (Stany Zjednoczone), zanim przekaż go do programu Microsoft Office Excel lub odczytać danych z kodu projektu.  
  
## <a name="considerations-for-storing-data"></a>Zagadnienia dotyczące przechowywania danych  
 Aby upewnić się, że prawidłowo interpretowane i wyświetlić dane, należy również rozważyć, czy problemy mogą wystąpić, gdy aplikacja jest przechowywane dane, takie jak formuły arkuszu programu Excel, w literałach ciągu (ustalony) zamiast w silnie typizowanych obiektów. Należy użyć danych sformatowanym przy założeniu stylu (Stany Zjednoczone) (identyfikator LCID wartość 1033) niezmiennej kultury lub angielskiej wersji językowej.  
  
### <a name="applications-that-use-string-literals"></a>Aplikacje, które używają literałów ciągów  
 Możliwe wartości, które mogą być ustalony obejmują literałów dat, zapisywanych w formacie angielski (Stany Zjednoczone) i formuły arkusza programu Excel, które zawierają nazwy zlokalizowanych funkcji. Inną możliwością może być ustalony ciąg, który zawiera wiele takich jak "1000"; w niektórych kultury to jest interpretowana jako tysiąca, ale w innych kultur reprezentuje jeden punkt zero. Obliczenia i porównania w niewłaściwym formacie może spowodować nieprawidłowe dane.  
  
 Interpretowane dowolne ciągi zgodnie z LCID, który jest przekazywany z ciągiem. Może to być spowodowane problemem, jeśli format ciągu nie odpowiada LCID, która została przekazana. Rozwiązania programu Excel utworzony za pomocą narzędzi programowania pakietu Office w Visual Studio Użyj 1033 LCID (en US) podczas przekazywania wszystkich danych. Powoduje wyświetlenie danych zgodnie z ustawieniami regionalnymi i językiem interfejsu użytkownika programu Excel. Visual Basic for Applications (VBA) działa także w ten sposób; Ciągi sformatowane jako en US i VBA prawie zawsze przekazuje 0 (niezależne od języka) jako identyfikator LCID. Na przykład następujący kod VBA wyświetla prawidłowo sformatowane wartości dla 12 maja 2004 zgodnie z bieżących ustawień regionalnych użytkownika:  
  
```  
'VBA  
Application.ActiveCell.Value2 = "05/12/04"  
```  
  
 Podczas formatowania daty w stylu en US, tego samego kodu, gdy jest używany w rozwiązaniu utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio i przekazywane do programu Excel COM interop daje takie same wyniki.  
  
 Na przykład:  
  
 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]  
  
 Powinien współpracować z silną kontrolą typów danych zamiast literałów ciągów, jeśli to możliwe. Na przykład zamiast daty są przechowywane w literale ciągu, zapisz go jako <xref:System.Double>, następnie przekonwertować go na <xref:System.DateTime> obiekt do manipulowania.  
  
 Poniższy przykładowy kod ma datę, która użytkownik wchodzi w komórce A5, przechowuje go jako <xref:System.Double>, następnie konwertuje go do <xref:System.DateTime> obiektu do wyświetlenia w komórce A7. Aby wyświetlić datę muszą być sformatowane A7 komórki.  
  
 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]  
  
### <a name="excel-worksheet-functions"></a>Funkcje arkusza programu Excel  
 Nazwy funkcji arkusza wewnętrznie przekładają się na większości wersji językowych programu Excel. Jednak ze względu na potencjalne języka i problemy międzyoperacyjne COM zdecydowanie zalecane jest używać nazwy funkcji tylko w języku angielskim w kodzie.  
  
### <a name="applications-that-use-external-data"></a>Aplikacje korzystające z danych zewnętrznych  
 Wszelki kod, który zostanie otwarty lub w przeciwnym razie używa danych zewnętrznych, takich jak pliki, które zawierają wartości rozdzielanych przecinkami (CSV pliki) wyeksportowany z starszej wersji systemu może również będzie zmienione, jeśli takie pliki są eksportowane formacie oprócz en US. Dostęp do bazy danych nie może być wpływu, ponieważ wszystkie wartości powinna być w formacie binarnym, chyba że baza danych przechowuje daty w postaci ciągów lub wykonuje operacje, które nie używają formatu binarnego. Ponadto można tworzyć zapytania SQL przy użyciu danych z programu Excel, należy upewnij się, że są one w formacie en US, w zależności od funkcji, do której należy użyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: docelowa Office wielojęzyczny interfejs użytkownika](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  