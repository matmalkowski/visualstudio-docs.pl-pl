---
title: "Lista dezasemblacji — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f37d62a906a0f528a821586470615a63f055af23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="list-disassembly-command"></a>Lista dezasemblacji — Polecenie
Rozpoczyna się proces debugowania i pozwala określić sposób obsługi błędów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Przełączniki  
 Każdy przełącznik może być wywoływany przy użyciu jego ukończenia formularza lub krótkich fragmentów.  
  
 / count: `number` [i] / / c: `number` [i] /length: `number` [i] / l: wyświetlenie`number`  
 Opcjonalny. Liczba instrukcji do wyświetlenia. Wartość domyślna to 8.  
  
 /endaddress: `expression` [i] / e:`expression`  
 Opcjonalny. Adres, w którym należy zatrzymać dezasemblacji.  
  
 /codebytes:`yes`&#124;`no` [i] /bytes:`yes`&#124;`no` [i] / b:`yes`&#124;`no`  
 Opcjonalny. Wskazuje, czy mają być wyświetlane bajtów kodu. Wartość domyślna to `no`.  
  
 / source:`yes`&#124;`no` [i] / s:`yes`&#124;`no`  
 Opcjonalny. Wskazuje, czy można wyświetlić kodu źródłowego. Wartość domyślna to `no`.  
  
 /symbolnames:`yes`&#124;`no` [i] /names:`yes`&#124;`no` [i] / n:`yes`&#124;`no`  
 Opcjonalny. Wskazuje, czy mają być wyświetlane nazwy symboli. Wartość domyślna to `yes`.  
  
 [/ linenumbers:`yes`&#124;`no`]  
 Opcjonalny. Umożliwia wyświetlanie numery wierszy związane z kodem źródłowym. Przełącznik/Source musi mieć wartość `yes` /linenumbers przełącznika.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Lista stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)   
 [Lista wątków — polecenie](../../ide/reference/list-threads-command.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)