---
title: Nowe polecenie Plik | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ad7f0232a4e08c134a7dffcc3d10a2180e235717
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="new-file-command"></a>Nowy plik — Polecenie
Tworzy nowy plik, a następnie go otwiera. Plik pojawi się w folderze dodatkowych plików.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalny. Nazwa pliku. Jeśli nazwa nie zostanie podany, podano nazwę domyślną. Jeśli żadna nazwa szablonu nie jest wyświetlane, jest tworzony plik tekstowy.  
  
## <a name="switches"></a>Przełączniki  
 / t:`templatename`  
 Opcjonalny. Określa typ pliku ma zostać utworzony.  
  
 / T:`templatename` argumentu składni odzwierciedla informacje znajdujące się w oknie dialogowym Nowy plik. Wprowadź nazwę kategorii, a następnie ukośnik odwrotny (`\`) i szablonu, nazwy i ująć cały ciąg w cudzysłowie.  
  
 Na przykład, aby utworzyć nową [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pliku źródłowego, należy wpisać następujący kod pod kątem / t:`templatename` argumentu.  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 W powyższym przykładzie oznacza, że szablon pliku C++ znajduje się w kategorii Visual C++ w **nowy plik** okno dialogowe.  
  
 / e:`editorname`  
 Opcjonalny. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.  
  
 / E:`editorname` argumentu składni korzysta z nazw Edytor znajdujące się w otwartych z okno dialogowe, ujęty w cudzysłów.  
  
 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy nową stronę sieci Web "test1.htm" i otwarcie go w edytorze kodu źródłowego.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Okno bezpośrednie](../../ide/reference/immediate-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)