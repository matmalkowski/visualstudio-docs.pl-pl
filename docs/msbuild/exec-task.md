---
title: Zadanie exec | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: "20"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0eadf1b5d94a136861d45275ebc5b94b6707cf14
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="exec-task"></a>Exec — Zadanie
Uruchamia określony program lub polecenia przy użyciu określonych argumentów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Exec` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Command`|Wymagane `String` parametru.<br /><br /> Polecenia do uruchomienia. Mogą to być polecenia systemowe, takie jak attrib, lub pliku wykonywalnego, takie jak program.exe, runprogram.bat lub setup.msi.<br /><br /> Ten parametr może zawierać wiele wierszy poleceń. Alternatywnie można umieścić wielu poleceń w pliku wsadowym i uruchomić go za pomocą tego parametru.|  
|`ConsoleOutput`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Każdy element danych wyjściowych jest wiersza ze Standardowy strumień wyjściowy lub błąd standardowy wyemitowany przez narzędzie. To jest tylko przechwycone, jeśli `ConsoleToMsBuild` ma ustawioną wartość `true`.|
|`ConsoleToMsBuild`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie będzie przechwytywać standardowy błąd i standardowe dane wyjściowe narzędzia i udostępnić je w `ConsoleOutput` parametru wyjściowego. Wartość domyślna to `false`.|
|`CustomErrorRegularExpression`|Opcjonalne `String` parametru.<br /><br /> Określa wyrażenie regularne, używany do wierszy dodatkowych błędów w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzia, które powodują powstanie niezwykle sformatowane dane wyjściowe.|  
|`CustomWarningRegularExpression`|Opcjonalne `String` parametru.<br /><br /> Określa wyrażenie regularne, który służy do dodatkowych wierszy ostrzeżenie w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzia, które powodują powstanie niezwykle sformatowane dane wyjściowe.|  
|`EchoOff`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie zostanie Emituj rozwinięte formę `Command` w dzienniku MSBuild. Wartość domyślna to `false`.|
|`ExitCode`|Opcjonalne `Int32` tylko do odczytu parametru wyjściowego.<br /><br /> Określa kod zakończenia zapewnianej przez wykonanego polecenia.|  
|`IgnoreExitCode`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie ignoruje kod zakończenia zapewnianej przez wykonanego polecenia. W przeciwnym razie zwraca zadanie `false` Jeśli wykonanego polecenia zwraca kod zakończenia inną niż zero.|  
|`IgnoreStandardErrorWarningFormat`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `false`, wybiera wiersze w danych wyjściowych, który jest zgodny z formatem standardowy błąd/ostrzeżenie i rejestruje je jako błędy lub ostrzeżenia. Jeśli `true`, wyłączyć to zachowanie. Wartość domyślna to `false`.|  
|`Outputs`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera elementy danych wyjściowych z zadania. `Exec` Zadania nie ustawia te samej siebie. Zamiast tego możesz podać je tak, jakby ona ustawiona, tak aby mogły być używane później w projekcie.|  
|`StdErrEncoding`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa kodowanie przechwyconych zadań Standardowy strumień błędów. Ustawieniem domyślnym jest bieżący konsoli kodowania danych wyjściowych.|  
|`StdOutEncoding`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa kodowanie przechwyconych zadania standardowego strumienia wyjściowego. Ustawieniem domyślnym jest bieżący konsoli kodowania danych wyjściowych.|  
|`WorkingDirectory`|Opcjonalne `String` parametru.<br /><br /> Określa katalog, w którym będzie uruchamiany polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 To zadanie jest przydatne w przypadku określonego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań dla zadania, które należy wykonać, nie są dostępne. Jednak `Exec` zadania, w przeciwieństwie do bardziej szczegółowych zadań, nie zebranie danych wyjściowych z narzędzia lub polecenia, że działa.  
  
 `Exec` Zadań wywołuje cmd.exe zamiast bezpośredniego wywoływania procesu.  
  
 Oprócz parametry wymienione w niniejszym dokumencie, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Exec` zadań, aby uruchomić polecenie.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
