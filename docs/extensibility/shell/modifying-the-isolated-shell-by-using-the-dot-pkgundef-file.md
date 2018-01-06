---
title: "Modyfikowanie przy użyciu programu Isolated Shell. Plik Pkgundef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 93eb993877d464f4303e0b49dc7219425c1a5f6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modyfikowanie przy użyciu programu Isolated Shell. Plik Pkgundef
Można zmodyfikować plik .pkgundef, aby wykluczyć wpisy rejestru określonego z aplikacji isolated shell. Zazwyczaj przy pierwszym uruchomieniu aplikacji na komputerze z powłoki programu Visual Studio kopiuje istniejące wpisy rejestru programu Visual Studio do głównego klucza rejestru dla aplikacji. W tym wszelkie odwołania do VSPackages aktualnie zainstalowany.  
  
 Aby wykluczyć określony wpis rejestru z aplikacji isolated shell, Dodaj do pliku .pkgundef aplikacji z klucza pakietu następuje zapis. Klucze i zapisy są reprezentowane tak jak w przypadku pliku .pkgdef; oznacza to jako [$RootKey$] lub [$RootKey$\\*podklucz*] i "*wpis*" =*wartość*, gdzie *podklucz* jest podklucz wpływa na, *wpis* wpisu do usunięcia, a *wartość* jest `""` lub `dword:00000000`.  
  
 Aby wykluczyć wiele wpisów z klucza rejestru, po prostu listy klucz jeden raz, znak wiersza dla każdego wpisu do wykluczenia.  
  
 Aby wykluczyć klucz rejestru całego z aplikacji isolated shell, Dodaj klucz do pliku .pkgundef aplikacji, ale nie należy określać wszystkie wpisy rejestru dla tego klucza.  
  
 Komentarze można dodawać do pliku .pkgundef. Komentarz jednowierszowy musi mieć dwa ukośniki jako pierwsze dwa znaki.  
  
 Na przykład, aby usunąć **Połącz z bazą danych** i **nawiązywanie połączenia z serwerem r** polecenia w **narzędzia** menu można Usuń komentarz z linii:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 i Dodaj wiersz:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 do pliku .pkgundef aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory GUID pakietu funkcje programu Visual Studio](package-guids-of-visual-studio-features.md)   
 [Dostosowywanie programu Isolated Shell](customizing-the-isolated-shell.md)