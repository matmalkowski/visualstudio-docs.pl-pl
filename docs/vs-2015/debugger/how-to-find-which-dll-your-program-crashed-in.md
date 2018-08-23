---
title: 'Porady: Odnajdywanie DLL, która nastąpiła awaria programu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dc06d433739b4c0706374a691474207a45c5766
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676704"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Porady: odnajdywanie biblioteki DLL, w której nastąpiła awaria programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Znajdź który biblioteki DLL Twój Program wystąpiła awaria w](https://docs.microsoft.com/visualstudio/debugger/how-to-find-which-dll-your-program-crashed-in).  
  
UWAGA]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Jeśli aplikacja ulegnie awarii podczas wywoływania biblioteki DLL systemu lub innej osoby kodu, musisz znaleźć się, które biblioteki DLL była aktywna podczas wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza własny program, można zidentyfikować lokalizację za pomocą **modułów** okna.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Aby dowiedzieć się, w przypadku, gdy awaria wystąpił podczas korzystania z okna modułów  
  
1.  Zanotuj adres, w których wystąpiła awaria.  
  
2.  Na **debugowania** menu, wybierz **Windows**i kliknij przycisk **modułów**.  
  
3.  W **modułów** oknie Znajdź **adres** kolumny. Może być konieczne sprawdzenie za pomocą paska przewijania.  
  
4.  Kliknij przycisk **adres** przycisku w górnej części kolumny, aby sortować biblioteki DLL przy użyciu adresu.  
  
5.  Skanowanie posortowaną listę można znaleźć biblioteki DLL, którego zakres adresów zawiera lokalizację awarii.  
  
6.  Przyjrzyj się **nazwa** i **ścieżki** kolumny, aby wyświetlić nazwę biblioteki DLL i ścieżkę.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: debugowanie natywnych bibliotek DLL](../debugger/how-to-debug-native-dlls.md)   
 [Porady: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)





