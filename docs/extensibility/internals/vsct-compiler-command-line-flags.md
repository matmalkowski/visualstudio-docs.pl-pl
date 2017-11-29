---
title: Flagi wiersza polecenia kompilatora VSCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd18d04adfbf3acd0ca50c1e75bd2a1694b28721
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vsct-compiler-command-line-flags"></a>Flagi wiersza polecenia kompilatora VSCT
Kompilator Visual Studio polecenia tabeli (VSCT) zawiera przełączniki wiersza polecenia w celu zapewnienia pomyślnej kompilacji vsct plików.  
  
## <a name="command-line-parameters"></a>Parametry wiersza polecenia  
 Aby wyświetlić pomoc podstawową VSCT z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **polecenia** okna, przejdź do *ścieżki instalacji programu Visual Studio SDK*folderu \VisualStudioIntegration\Tools\Bin\ i wpisz:  
  
```  
vsct /?  
```  
  
 To polecenie zwróci:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Znaki — (dash) i / (ukośnik) są zarówno zatwierdzone notacji wskazujące parametry wiersza polecenia.  
  
 Dopuszczalne flagami obiektów i ich znaczenie są.  
  
|Przełącznik|Opis|  
|------------|-----------------|  
|-D|Określ wszelkie dodatkowe zdefiniowanych symboli.|  
|-I|Wskazują, że dodatkowy obejmują ścieżek, które powinny być używane podczas rozpoznawania odwołań do pliku.|  
|-L|Określ <xref:System.Globalization.CultureInfo> nazwa kultury, na przykład "en US".|  
|-E|Emituj obiektów C# w określonej przestrzeni nazw dla elementów polecenia, a następnie [C &#124; P &#124;N]:*filename*gdzie C = C#, H = nagłówka C++, N przestrzeń nazw =. Przestrzeń nazw jest wymagany dla języka C#.|  
|-v|Pełne dane wyjściowe.|  
  
 Przełącznika -L instruuje kompilator, aby wybrać grupę ciągów w celu utworzenia pliku binarnego .cto, który odpowiada danym <xref:System.Globalization.CultureInfo> nazwa kultury. Określona nazwa kultury powinna być zgodna atrybut Language co najmniej jednego [Element ciągów](../../extensibility/strings-element.md) w pliku vsct. Jeśli element ciągów nie ma języka atrybutu, został on odziedziczony po zawierający [CommandTable elementu](../../extensibility/commandtable-element.md).  
  
 Pliku vsct może mieć wielu elementów ciągów, a każdy może mieć inny atrybut języka. Globalizacja jest to osiągane przez wielokrotnego uruchamiania kompilatora VSCT i zmiana przełącznika -L dla każdej nazwy kultury.  
  
 Podana nazwa kultury przez przełącznik -L niezgodny atrybut języka dowolnego elementu ciągi kompilator będzie podjąć próbę dopasowania język, a nie region. Na przykład jeśli nie można odnaleźć "pl pl", kompilator zamiast spróbuje "en". W przypadku braku, spróbuje bieżącej kultury systemu operacyjnego. Kończą się niepowodzeniem zostanie on kompilacji pierwszy element ciągi znalezione.  
  
 Przełącznika -E może służyć do Emituj plik nagłówka stylu języka C, który zawiera symbole, które są używane przez tabelę polecenia lub do wysyłania pliku C#, który zawiera obiekty symboli polecenia.  
  
 -D i - I przełączniki mają składni preprocesora Cl.exe C flag, które mają taką samą nazwę. -D definicje, które mają format X = Y używanych dla rozszerzenia opartych na języku XML \<zdefiniowane > testów w `Condition` atrybutów. -Ścieżki dołączanych plików I służą do rozpoznawania \<Include >, \<Extern > i \<mapy bitowej > pliku odwołania. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Kompilator VSCT można również dekompilować wcześniej skompilowany plik binarny. Aby to zrobić, należy dostarczyć plik binarny dla \<PlikWejściowy >.   Plik binarny został utworzony przez kompilator VSCT, będzie miał jego symbole już osadzonych i będzie generowania danych wyjściowych z nazwy symbolicznej \<symbole > sekcji danych wyjściowych. Plik binarny został utworzony przez kompilator CTC, dane wyjściowe będą zawierać rzeczywistych identyfikatorów GUID i identyfikatorów. Plik *.ctsym utworzonym przez bieżące wersje Ctc.exe znajduje się w tym samym folderze co plik binarny wejściowych, symbole zostanie załadowany z tego pliku i używane dla danych wyjściowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)   
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)