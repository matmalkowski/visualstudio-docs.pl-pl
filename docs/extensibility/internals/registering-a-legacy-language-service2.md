---
title: Rejestrowanie klienta2 języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cb7750f55bd9175c552aa765d21b1334f5f1dfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="registering-a-legacy-language-service"></a>Zarejestrowanie starsza wersja usługi języka
Poniższe sekcje zawierają listę wpisy rejestru dla różnych języków usługi opcje dostępne w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Na poniższej liście wpisy rejestru *katalogu głównego rejestru VS* jest równa HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, gdzie *X.Y* jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numer wersji.  
  
## <a name="registry-entries-for-language-service-options"></a>Wpisy rejestru dotyczące opcji usługi języka  
 *Katalogu głównego rejestru VS*usług \Languages\Language\\*nazwy języka* klucz może zawierać następujące wartości.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|*\<IDENTYFIKATOR GUID &GT;*|Identyfikator GUID usługi języka.|  
|LangResID|REG_DWORD|0x0 0xffff|Ciąg identyfikatora zasobów (ResID) dla nazwy zlokalizowany tekst języka.|  
|Package|REG_SZ|*\<IDENTYFIKATOR GUID &GT;*|Identyfikator GUID pakietu VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Określa, czy **uzupełniania** opcje w **opcje** okno dialogowe są włączone.|  
|ShowSmartIndent|REG_DWORD|0-1|Określa, czy wybrać opcję **inteligentne** wcięcia w **opcje** okno dialogowe jest włączona.|  
|RequestStockColors|REG_DWORD|0-1|Określa, czy niestandardowego lub domyślnego kolory Kolor słów kluczowych.|  
|ShowHotURLs|REG_DWORD|0-1|Określa, czy użytkownik może kliknąć adresów URL.|  
|Domyślnie nie gorących adresy URL|REG_DWORD|0-1|Określa ustawienie początkowej **włączyć nawigację adresów URL jednym kliknięciem** opcji **opcje** — okno dialogowe.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Określa, czy usługa języka ma "wstawiaj odstępy" jako jego opcji karty domyślnej.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Włącza lub wyłącza **pasek nawigacyjny** opcji **opcje** okno dialogowe, które pokazuje lub ukrywa **pasek nawigacyjny**.|  
|Tylko jeden kod okna|REG_DWORD|0-1|Włącza lub wyłącza **nowe okno** choice w **okna** menu dla usługi języka.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Włącza lub wyłącza **opcje** ustawienie okno dialogowe dla **Ukryj zaawansowane członków**.|  
|Obsługa CF_HTML|REG_DWORD|0-1|Określa, czy edytor umożliwia kopiowanie i wklejanie danych HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Określa, czy **numerów linii** opcje w **opcje** okno dialogowe jest włączone dla usługi języka.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Określa, czy członków zaawansowanych, takich jak prywatny pola są ukryte na listach uzupełniania.|  
|ShowBraceCompletion|REG_DWORD|0-1|Określa, czy **nawiasy ukończenia** opcji w **opcje** okno dialogowe jest włączona.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>Wpisy rejestru dotyczące języków — opcje debugera  
 *Katalogu głównego rejestru VS*usług \Languages\Language\\*nazwy języka*\Debugger języków\\*GUID*\ klucz może uwzględniać następujące wartości.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|tekst|Wartość domyślna może służyć do nazwę języka dokumentu. Nazwa tego klucza jest identyfikatorem GUID ewaluatora wyrażeń, który ma odpowiadający mu wpis w  *\<katalogu głównego rejestru VS >*\AD7Metrics\Expression ewaluatora.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Wpisy rejestru dotyczące opcji narzędzi edytora  
 Możesz dodać klucze rejestru w kluczu EditorToolsOptions strony właściwości i węzły właściwości. Te klucze i wartości zidentyfikować strony właściwości w **opcje** okno dialogowe (na **narzędzia** menu) służące do konfigurowania usługi języka. W poniższym przykładzie *nazwy strony* jest nazwą strony właściwości i *nazwa węzła* jest nazwa węzła drzewa na **opcje** okno dialogowe. Wpis strony i wejście węzła należy określić osobno.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|resID|Nazwa zlokalizowanej wyświetlania tej strony opcji. Nazwa może być literały tekstowe lub #`nnn`, gdzie `nnn` jest identyfikator zasobu ciągu w satelitarnej biblioteki DLL z określonym pakiecie VSPackage.|  
|Package|REG_SZ|*IDENTYFIKATOR GUID*|Identyfikator GUID pakiet VSPackage, który implementuje ta strona Opcje.|  
|Strona|REG_SZ|*IDENTYFIKATOR GUID*|Identyfikator GUID strony właściwości do żądania od pakiet VSPackage, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody. Jeśli tego wpisu rejestru nie jest obecny, klucz rejestru opisuje węzeł, nie strony.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>Wpisy rejestru dla opcji rozszerzenia nazwy pliku  
 Wpis dla rozszerzenia pliku powinna być poprzedzone kropką, na przykład ".myext".  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|*IDENTYFIKATOR GUID*|Identyfikator GUID usługi dla usługi języka domyślnego dla tego typu rozszerzenia nazwy pliku.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Wpisy rejestru dotyczące opcji edytora  
 *Katalogu głównego rejestru VS*\Editors klucz może zawierać następujące wartości:  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|""|Nieużywane; Możesz umieścić tutaj swoje imię dokumentacji.|  
|DefaultToolboxTab|REG_SZ|""|Nazwa na karcie przybornika, aby ustawić domyślną, gdy edytora jest aktywny.|  
|Nazwa wyświetlana|REG_SZ|resID|Nazwa do wyświetlenia w **Otwórz za pomocą** okno dialogowe. Nazwa jest identyfikator zasobu ciągu lub nazwę w standardowym formacie.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Używany do **Otwórz za pomocą** polecenia menu. Jeśli nie chcesz listy domyślny edytor tekstu na liście dostępnych edytory dla określonego typu pliku, ta wartość 1.|  
|LinkedEditorGUID|REG_SZ|*\<IDENTYFIKATOR GUID &GT;*|Używane dla żadnej usługi języka, który można otworzyć pliku z obsługą stronę kodową. Na przykład po otwarciu pliku txt przy użyciu **Otwórz za pomocą** polecenia i opcje są dostępne za pomocą edytora kodu źródłowego z lub bez kodowania.<br /><br /> GUID określony nazwach podklucz jest strona kodowa fabryki edytora; połączony identyfikator GUID określony w ten wpis rejestru jest fabryki edytora regularne. Celem tego wpisu jest, że IDE nie można otworzyć pliku przy użyciu domyślnego edytora, IDE będzie próbować użyć edytora dalej na liście. Ten edytor dalej nie powinien być fabryki edytora stronę kodową, ponieważ tej fabryki edytora jest zasadniczo taki sam, jak fabryki edytora, które zakończyły się niepowodzeniem.|  
|Package|REG_SZ|*\<IDENTYFIKATOR GUID &GT;*|Identyfikator GUID pakietu VSPackage ResID nazwę wyświetlaną.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>Wpisy rejestru dotyczące opcji widoku logicznym  
 *Katalogu głównego rejestru VS*\Editors\\*graficznego interfejsu użytkownika edytora >*\LogicalViews klucz może zawierać następujące wartości.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ||Nieużywane.|  
|*\<IDENTYFIKATOR GUID &GT;*|REG_SZ|""|Klucz do logicznych widoków obsługiwane. Może mieć jako wiele z tych zgodnie z potrzebami. Nazwa wpisu rejestru to, co jest ważne, nie wartość, która jest zawsze ciągiem pustym.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>Wpisy rejestru dla opcji rozszerzenia Edytora  
 *Katalogu głównego rejestru VS*\Editors\\*GUID edytor*\Extensions klucz może zawierać następujące wartości. Rozszerzenie nazwy pliku nie być poprzedzone kropką.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ||Nieużywane.|  
|*\<ext >*|REG_DWORD|0 0xffffffff|Względny priorytet rozszerzenia. Jeśli dwa lub więcej języków mają te same rozszerzeń, zostanie wybrany język wyższy priorytet.|  
  
 Ponadto, wybór domyślny bieżącego użytkownika dla edytora znajduje się w HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default edytory\\*ext*. Identyfikator GUID usługi wybrany język jest we wpisie niestandardowe. To ma pierwszeństwo przed dla bieżącego użytkownika.  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Wpisy rejestru dotyczące opcji usługi języka Framework zarządzanego pakietu  
 Następujące wpisy rejestru są specyficzne dla klasy usługi języka framework (MPF) zarządzanego pakietu. Te wpisy rejestru wskazują pomocy technicznej w usłudze języka dla różnych funkcji IntelliSense i inne zaawansowane funkcje edycji.  
  
 Te wpisy rejestru są dostępne za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Obsługa operacji IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Obsługa języka par takich jak nawiasy klamrowe, nawiasy i nawiasy.|  
|Skrócone informacje|REG_DWORD|0-1|Obsługa operacji szybkie informacje funkcji IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Obsługa wyświetlania kompletnej pary języka na pasku stanu.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Obsługa wyświetlania zgodnych kierunki, zazwyczaj przez wyróżnianie dwa elementy.|  
|MaxErrorMessages|REG_DWORD|0-n|Maksymalna liczba błędów, które mogą być wyświetlane w **listy błędów** okna.|  
|CodeSenseDelay|REG_DWORD|0-n|Wyrażony w milisekundach czas opóźnienia przed rozpoczęciem wszelkich tła podczas analizowania operacji IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Obsługa analizowanie w tle.|  
|EnableCommenting|REG_DWORD|0-1|Obsługa komentowania limit wybrane bloki tekstu i oznacza także obsługę Trwa usuwanie komentarza zaznaczonego tekstu.|  
|EnableFormatSelection|REG_DWORD|0-1|Obsługa formatowania tekstu, takich jak automatyczne wcięcie lub dostosowania pozycji nawiasów klamrowych.|  
|AutoOutlining|REG_DWORD|0-1|Obsługa zwijania (regionach, które może zostać zwinięty).|  
|MaxRegions|REG_DWORD|0-n|Maksymalna liczba ukryte obszary na plik.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)