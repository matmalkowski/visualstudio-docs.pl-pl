---
title: Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7da9446a4a5e4538164b09d1f11733f7bde3de24
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693360"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office
  Zabezpieczenia zapewniane przez program Microsoft .NET Framework i program Microsoft Office może pomóc chronić przed zagrożeniami bezpieczeństwa możliwych rozwiązań pakietu Office. W tym temacie opisano niektóre z tych zagrożeń i zawiera zalecenia w celu ochrony przed nimi. Zawiera także informacje o wpływie ustawienia zabezpieczeń Microsoft Office na rozwiązań pakietu Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Zaufany kod jest zmiany przeznaczenia w dokumencie nowego, niebezpiecznego  
 Może potrwać zaufanego kodu, który jest przeznaczony dla jednego określonego celu, na przykład pobieranie informacji osobistych dla aplikacji zatrudnienia, a użyć go ponownie w innym dokumencie, takie jak arkusza. Kod nie może określić, czy oryginalnego dokumentu nie jest uruchomiona i może otworzyć innych zagrożeń, takich jak ujawniania informacji osobistych lub wykonywanie kodu z uprawnieniami zwiększona, gdy otwarty przez innego użytkownika. Alternatywnie osoba atakująca wystarczy zmodyfikować danych w arkuszu tak, aby przy wysyłaniu do ofiary, zachowuje nieoczekiwanie. Zmiana wartości, formuły lub prezentacji właściwości arkusza powiązane z kodem, istnieje możliwość złośliwy użytkownik na ataki innego użytkownika, wysyłając zmodyfikowany plik. Może być również użytkownikom uzyskiwanie dostępu do informacji, który nie powinien Zobacz przez zmodyfikowanie wartości w tym skoroszycie.  
  
 Ponieważ zarówno w lokalizacji zestawu, jak i lokalizację dokumentu musi mieć wystarczające materiały do wykonania, atak nie jest łatwo zainstalować. Na przykład dokumenty w załączników wiadomości e-mail lub w niezaufanej intranetowe serwery nie masz wystarczających uprawnień do uruchomienia.  
  
 Aby umożliwić atak kodu musi być napisana w taki sposób, fakt, że decyzje na podstawie danych potencjalnie niezaufanym. Przykładem jest utworzenie arkusz ma ukryte komórki, która zawiera nazwę serwera bazy danych. Użytkownik przesyła arkusza do strony ASPX, który próbuje połączyć się z tym serwerem przy użyciu uwierzytelniania programu SQL i hasło administratora systemu ustalony. Osoba atakująca może zastąpić zawartość komórki ukryte inną nazwę komputera i uzyskać hasło administratora systemu. Aby uniknąć tego problemu, nigdy nie kodowane hasła i sprawdzać identyfikatorów serwera przed wewnętrzną listę serwerów, które są znane jako dobra przed uzyskaniem dostępu do serwera.  
  
### <a name="recommendations"></a>Zalecenia  
  
-   Sprawdzanie poprawności danych wejściowych i danych, czy pochodzi od użytkownika, dokument, bazy danych, usługi sieci web lub dowolnego innego źródła.  
  
-   Należy rozważnie udostępnianie określonych typach funkcje, takie jak pobieranie danych uprzywilejowanych w imieniu użytkownika i umieścić go w niechronionego arkusza.  
  
-   W zależności od typu aplikacji może być uzasadnione, aby sprawdzić, czy działa oryginalnego dokumentu, przed wykonaniem jakiegokolwiek kodu. Na przykład sprawdzić, czy działa z dokumentu przechowywanego w lokalizacji znane, bezpieczne.  
  
-   Może być dobrym pomysłem jest wyświetlone ostrzeżenie o po otwarciu dokumentu, jeśli aplikacja przeprowadza wszelkie uprzywilejowanych akcji. Na przykład utworzyć ekran powitalny lub okna dialogowego Uruchamianie informujący o tym, czy aplikacja będzie dostęp do informacji osobistych, a użytkownik powinien wybrać kontynuować, lub Anuluj. Jeśli użytkownik końcowy pobiera takie ostrzeżenie z pozornie nieszkodliwie dokumentu, użytkownik będzie można zamyka aplikację, zanim zostanie naruszony niczego.  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod jest zablokowany przez strażnik modelu obiektów programu Outlook  
 Microsoft Office może uniemożliwić używanie niektórych właściwości, metod i obiektów w modelu obiektów kodu. Przez ograniczenie dostępu do tych obiektów, Outlook pomaga zapobiec użyciu object model dla celów złośliwego robaki poczty e-mail i wirusami. Ta funkcja zabezpieczeń jest określany jako strażnik modelu obiektów programu Outlook. Jeśli dodatku VSTO próbuje użyć ograniczone właściwości lub metody, gdy włączone jest strażnik modelu obiektów, Outlook wyświetli ostrzeżenie, który umożliwia użytkownikowi zatrzymać operację lub umożliwia użytkownikowi udzielić dostępu do właściwości lub metody ograniczony okres czas. Jeśli użytkownik zatrzymuje operację, zgłosi dodatków VSTO programu Outlook utworzony przy użyciu rozwiązań pakietu Office w Visual Studio <xref:System.Runtime.InteropServices.COMException>.  
  
 Strażnik modelu obiektów może wpływać na dodatków VSTO na różne sposoby, w zależności od tego, czy program Outlook jest używany z programem Microsoft Exchange Server:  
  
-   Jeśli program Outlook nie jest używany z programem Exchange, administrator można włączyć lub wyłączyć strażnik modelu obiektów dla wszystkie dodatki VSTO na komputerze.  
  
-   Jeśli program Outlook jest używany z programem Exchange, administrator może włączyć lub wyłączyć strażnik modelu obiektów dla wszystkie dodatki VSTO na komputerze lub administrator może określić, że niektóre dodatków VSTO może działać bez napotkania strażnik modelu obiektów. Administratorzy mogą również modyfikowanie strażnik modelu obiektów dla niektórych obszarach model obiektów. Na przykład Administratorzy mogą automatycznie umożliwić dodatków VSTO programowe, wysłanie wiadomości e-mail, nawet jeśli włączono strażnik modelu obiektów.  
  
 Począwszy od programu Outlook 2007, zachowanie strażnik modelu obiektów został zmieniony zwiększające deweloperów i środowisko użytkownika podczas pomaga zapewnić bezpieczeństwo programu Outlook. Aby uzyskać więcej informacji, zobacz [kodu zmiany zabezpieczeń w programie Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### <a name="minimize-object-model-guard-warnings"></a>Minimalizowanie ostrzeżenia strażnik modelu obiektów  
 Aby uniknąć ostrzeżenia o zabezpieczeniach podczas korzystania z ograniczeniami właściwości i metody, upewnij się, Twoje dodatku VSTO uzyskuje obiektów programu Outlook z `Application` pole `ThisAddIn` klasy w projekcie. Aby uzyskać więcej informacji dotyczących tego pola, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
 Strażnik modelu obiektów mogą ufać tylko obiekty Outlook uzyskany z tego obiektu. Z kolei obiekty, które są uzyskiwane z nową `Microsoft.Office.Interop.Outlook.Application` obiektu nie są zaufane i ograniczeniami właściwości i metody zgłosi ostrzeżenia o zabezpieczeniach włączenie strażnik modelu obiektów.  
  
 Poniższy przykład kodu wyświetli ostrzeżenie, jeśli włączono strażnik modelu obiektów. `To` Właściwość `Microsoft.Office.Interop.Outlook.MailItem` klasy jest ograniczony przez strażnik modelu obiektów. `Microsoft.Office.Interop.Outlook.MailItem` Obiekt jest niezaufanych, ponieważ kod pobiera z `Microsoft.Office.Interop.Outlook.Application` utworzonego przy użyciu **nowe** operatora, zamiast z uzyskiwania `Application` pola.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 Poniższy przykład kodu pokazuje sposób użycia ograniczeniami do właściwości `Microsoft.Office.Interop.Outlook.MailItem` obiektu, który jest uznawany za zaufany przez strażnik modelu obiektów. W kodzie użyto zaufanych `Application` pola, aby uzyskać `Microsoft.Office.Interop.Outlook.MailItem`.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Jeśli program Outlook jest używany z programem Exchange, uzyskiwanie wszystkich obiektów programu Outlook z `ThisAddIn.Application` nie gwarantuje, że z dodatku VSTO będą mogli uzyskać dostępu do całej modelu obiektów programu Outlook. Na przykład jeśli administrator programu Exchange Outlook automatycznie ustawia Odmów wszystkie próby dostępu do informacji o adresie za pomocą modelu obiektów programu Outlook, a następnie Outlook nie pozwoli na poprzednim przykładzie kodu do uzyskania dostępu do właściwości, mimo że przykładzie kodu używane zaufany `ThisAddIn.Application` pola.  
  
### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Określ, które dodatki do sytuacji, gdy za pomocą programu Exchange  
 Gdy program Outlook jest używany z programem Exchange, Administratorzy mogą określić, że niektóre dodatków VSTO może działać bez napotkania strażnik modelu obiektów. Dodatki programu Outlook VSTO utworzony przy użyciu rozwiązań pakietu Office w Visual Studio nie może być zaufane indywidualnie. może być tylko zaufane jako grupa.  
  
 Outlook ufa dodatku VSTO oparte na wartość skrótu wpis punktu pliku DLL dodatku VSTO. Wszystkie VSTO programu Outlook dodatki przeznaczonych [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] użycie tej samej biblioteki DLL punktu wejścia (*VSTOLoader.dll*). Oznacza to, że jeśli administrator ufa żadnych dodatku VSTO przeznaczonego [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] działać bez napotkania strażnik modelu obiektów, a następnie wszystkie inne VSTO dodatki, które dotyczy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] również są zaufane. Aby uzyskać więcej informacji na temat ufające określonych VSTO dodatki do uruchomienia bez napotkania strażnik modelu obiektów, zobacz [określić metodę Outlook używa do zarządzania funkcji ochrony przed wirusami](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>Zmiany uprawnień nie będą obowiązywać natychmiast  
 Jeśli administrator dopasowuje uprawnienia do dokumentu lub zestawu, użytkowników, należy zamknąć i uruchom ponownie wszystkie aplikacje pakietu Office, aby te zmiany mają być egzekwowane.  
  
 Inne aplikacje obsługujące aplikacje Microsoft Office może uniemożliwić również nowe uprawnienia z wymuszany. Użytkownikom należy Zamknij wszystkie aplikacje, korzystających z pakietu Office, hostowanej lub autonomiczne, zmiana zasad zabezpieczeń.  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Ustawienia Centrum zaufania Microsoft Office System nie wpływają na dodatki lub dostosowywanie na poziomie dokumentu  
 Użytkownicy mogą uniemożliwić dodatków VSTO ładowanie przez ustawienie opcji **Centrum zaufania**. Jednak dodatków VSTO i dostosowań na poziome dokumentu utworzony przy użyciu rozwiązań pakietu Office w Visual Studio nie dotyczy tych ustawień zaufania.  
  
 Jeśli użytkownik uniemożliwia dodatków VSTO ładowania przy użyciu **Centrum zaufania**, nie zostanie załadowany następujące typy dodatków VSTO:  
  
-   Zarządzane i niezarządzane COM VSTO dodatki.  
  
-   Dokumenty inteligentne zarządzane i niezarządzane.  
  
-   Zarządzane i niezarządzane VSTO automatyzacji dodatki.  
  
-   Składniki zarządzane i niezarządzane danych w czasie rzeczywistym.  
  
 W poniższych procedurach opisano, jak użytkownicy mogą używać **Centrum zaufania** aby uniemożliwić dodatków VSTO obciążenia w programie Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i Microsoft Office 2010. Te procedury będą miały wpływu na dodatków VSTO lub dostosowania utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio.  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Aby wyłączyć dodatków VSTO w Microsoft Office 2010 i Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikacji  
  
1.  Wybierz **pliku** kartę.  
  
2.  Wybierz *ApplicationName* **opcje** przycisku.  
  
3.  W okienku Kategorie wybierz **Centrum zaufania**.  
  
4.  W okienku szczegółów wybierz **ustawienia Centrum zaufania**.  
  
5.  W okienku Kategorie wybierz **dodatki**.  
  
6.  W okienku szczegółów wybierz **dodatki wymagają aplikacji były podpisane przez zaufanego wydawcę** lub **Wyłącz wszystkie dodatki aplikacji**.  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  