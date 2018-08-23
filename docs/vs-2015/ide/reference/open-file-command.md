---
title: Otwórz plik — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51be74b491ee9a45cfac4735332146b9c5ffb06d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683962"
---
# <a name="open-file-command"></a>Otwórz plik — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenia Otwórz plik](https://docs.microsoft.com/visualstudio/ide/reference/open-file-command).  
  
  
Otwiera istniejący plik i pozwala na określenie edytora.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagane. Pełnej lub częściowej ścieżkę i nazwę pliku, aby otworzyć. Ścieżki zawierające spacje muszą być ujęte w znaki cudzysłowu.  
  
## <a name="switches"></a>Przełączniki  
 / e:`editorname`  
 Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.  
  
 / E:`editorname` argument składni używa nazw edytora, w jakiej występują w Otwórz za pomocą okno dialogowe, ujęta w znaki cudzysłowu.  
  
 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy wprowadzasz ścieżkę, automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera plik styl "Test1.css" w edytorze kodu źródłowego.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Okno bezpośrednie](../../ide/reference/immediate-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



