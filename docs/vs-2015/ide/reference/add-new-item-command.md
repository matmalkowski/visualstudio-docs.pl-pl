---
title: Dodaj nowy element polecenie | Dokumentacja firmy Microsoft
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
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f380a11440ed413871d2c80603148aa7cc77390
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42692259"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Dodaj nowy element — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/add-new-item-command).  
  
  
Dodaje nowy element rozwiązania, takie jak .htm, CSS, txt lub zestaw ramek do bieżącego rozwiązania i otwiera go.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalna. Ścieżka i nazwa pliku elementu do dodania do rozwiązania.  
  
## <a name="switches"></a>Przełączniki  
 t: `templatename`  
 Opcjonalna. Określa typ pliku ma zostać utworzony. Jeśli nazwa szablonu nie zostanie określony, domyślnie tworzone jest plikiem tekstowym.  
  
 T:`templatename` składnię argumentu odzwierciedla informacji znajdujących się w **Dodaj nowy element rozwiązania** okno dialogowe. Należy wprowadzić pełną kategorii, typu pliku, oddzielając nazwy kategorii z typu pliku za ukośnik odwrotny, po którym następuje (`\`) i nawiasami cały ciąg w cudzysłowie.  
  
 Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujące t:`templatename` argumentu.  
  
```  
/t:"General\Style Sheet"  
```  
  
 / e: `editorname`  
 Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.  
  
 / E:`editorname` składnię argumentu używa nazw edytora, w jakiej występują w **Otwórz okno dialogowe za pomocą**, ujęty w znaki cudzysłowu.  
  
 Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład dodaje nowy element rozwiązania, MyHTMLpg, do bieżącego rozwiązania.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



