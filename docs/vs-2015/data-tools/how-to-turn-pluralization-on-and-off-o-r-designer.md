---
title: 'Porady: Włączanie pluralizacja włączać i wyłączać (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 02fa8b50b28f967a0835f68e85d146ca1eea514b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689160"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Porady: Włączanie pluralizacja włączać i wyłączać (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Włączanie pluralizacja włączać i wyłączać (Projektant O-R)](https://docs.microsoft.com/visualstudio/data-tools/how-to-turn-pluralization-on-and-off-o-r-designer).  
  
  
Domyślnie podczas przeciągania obiektów bazy danych, które mają nazwy kończące się na s lub ię od **Eksploratora serwera**/**Eksplorator bazy danych** na [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazwy wygenerowanych klas jednostek zostaną zmienione w liczbie mnogiej na liczbę pojedynczą. W ten sposób bardziej przedstawiać fakt, że klasa wystąpień jednostki mapowany na pojedynczy rekord danych. Na przykład dodanie tabeli Customers [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wyniki w klasie jednostki o nazwie odbiorcy, ponieważ klasa przechowuje dane dla jednego klienta.  
  
> [!NOTE]
>  Pluralizacja jest domyślnie tylko w języku angielskim wersji programu Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć pluralizacja włączać i wyłączać  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okna dialogowego rozwiń **narzędzia graficzne bazy danych**.  
  
> [!NOTE]
>  Wybierz **Pokaż wszystkie ustawienia** Jeśli **narzędzia graficzne bazy danych** węzeł nie jest widoczny.  
  
1.  Kliknij przycisk **O/R Designer**.  
  
2.  Ustaw **Pluralizację nazw** do **włączone** = **False** można ustawić [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tak, aby nie zmienia nazwy klas.  
  
3.  Ustaw **Pluralizację nazw** do **włączone** = **True** mają dotyczyć zasady pluralizacja nazw klasy obiekty dodane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

