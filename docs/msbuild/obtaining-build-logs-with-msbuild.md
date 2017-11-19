---
title: "Uzyskiwanie kompilacji dzienników przy użyciu programu MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: "27"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: cd7e50a44e5d53653f233372b643c31fe58aedc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="obtaining-build-logs-with-msbuild"></a>Uzyskiwanie dzienników kompilacji za pomocą narzędzia MSBuild
Za pomocą przełączników przy użyciu programu MSBuild, można określić, ile danych kompilacji, aby przeglądu i określa, czy chcesz zapisać dane kompilacji do jednego lub więcej plików. Można również określić niestandardowe rejestratora zbierania danych kompilacji. Aby uzyskać informacje dotyczące przełączników wiersza polecenia programu MSBuild, których nie opisano w tym temacie, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  W przypadku tworzenia projektów za pomocą środowiska IDE programu Visual Studio, można rozwiązać te kompilacji, przeglądając dzienniki kompilacji. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Ustawienie poziomu szczegółowości  
 Podczas tworzenia projektu za pomocą MSBuild bez określania poziomu szczegółowości, w dzienniku danych wyjściowych pojawia się następujące informacje:  
  
-   Błędy, ostrzeżenia i komunikaty, które są sklasyfikowane jako bardzo ważne.  
  
-   Niektóre zdarzenia stanu.  
  
-   Podsumowanie kompilacji.  
  
 Za pomocą **/verbosity** (**/v**) przełącznika, można kontrolować, ile danych pojawia się w dzienniku danych wyjściowych. Do rozwiązywania problemów, użyj poziomu szczegółowości albo `detailed` (`d`) lub `diagnostic` (`diag`), zapewniający najwięcej informacji.  
  
 Proces kompilacji może przebiegać wolniej, ustawiając **/verbosity** do `detailed` , a nawet wolniejsze w przypadku ustawienia **/verbosity** do `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Zapisywanie dziennika kompilacji do pliku  
 Można użyć **/fileLogger** (**fl**) przełącznik, aby zapisać w pliku danych kompilacji. Poniższy przykład zapisuje dane kompilacji w pliku o nazwie `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 W poniższym przykładzie plik dziennika o nazwie `MyProjectOutput.log`, a poziom szczegółowości danych wyjściowych dziennika jest ustawiona na `diagnostic`. Określ te dwa ustawienia za pomocą **/filelogparameters** (`flp`) przełącznika.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Aby uzyskać więcej informacji, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Zapisywanie dziennika danych wyjściowych do wielu plików  
 Poniższy przykład jest zapisywany cały dziennik, aby `msbuild1.log`, tylko błędy na `JustErrors.log`i po prostu ostrzeżenia do `JustWarnings.log`. W przykładzie użyto numerów plików dla każdego z trzech plików. Numery pliku są określone tuż po **/fl** i **/flp** przełączników (na przykład `/fl1` i `/flp1`).  
  
 **/Filelogparameters** (`flp`) zmienia określić pliki, 2 i 3 co nazwa każdego pliku oraz elementów do uwzględnienia w każdym pliku. Nie określono nazwy dla pliku 1, więc domyślną nazwę `msbuild1.log` jest używany.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Aby uzyskać więcej informacji, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Korzystając z niestandardowego urządzenia zapisującego ciąg akcji  
 Można pisać własne rejestratora przy tworzenia zarządzanego typu, który implementuje <xref:Microsoft.Build.Framework.ILogger> interfejsu. Można na przykład Rejestrator niestandardowych, na przykład wysłać błędy kompilacji w wiadomości e-mail, ich logowania do bazy danych lub dziennika je do pliku XML. Aby uzyskać więcej informacji, zobacz [rejestratory kompilacji](../msbuild/build-loggers.md).  
  
 W wierszu polecenia programu MSBuild określ rejestrator niestandardowych za pomocą **/logger** przełącznika. Można również użyć **/noconsolelogger** przełącznik, aby wyłączyć domyślnego rejestratora konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Rejestrowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)