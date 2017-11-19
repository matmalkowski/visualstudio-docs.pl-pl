---
title: "Porady: Włączanie określania liczby mnogiej i wyłączanie (Projektant O-R) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 87779cb647e00c990f4f8b29907a0dc344b80f42
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Porady: Włączanie określania liczby mnogiej i wyłączanie (Projektanta obiektów relacyjnych)
Domyślnie podczas przeciągania obiektów bazy danych, które mają nazwy kończące się s lub IE z **Eksploratora serwera**/**Eksploratora bazy danych** na [składnika LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazw wygenerowanych klas jednostek nie zostaną zmienione w liczbie mnogiej na liczbę pojedynczą. To jest bardziej przedstawiać fakt, że klasa jednostki wystąpień mapuje pojedynczy rekord danych. Na przykład dodawania tabeli klientów do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wyniki w klasie jednostki o nazwie odbiorcy, ponieważ klasa będą przechowywane dane tylko jednego odbiorcy.  
  
> [!NOTE]
>  Pluralizacja jest domyślnie tylko w języku angielskim wersji programu Visual Studio.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć określania liczby mnogiej lub wyłączyć  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okna dialogowego rozwiń **narzędzi bazy danych**.  
  
    > [!NOTE]
    >  Wybierz **Pokaż wszystkie ustawienia** Jeśli **narzędzi bazy danych** węzeł nie jest widoczne.  
  
3.  Kliknij przycisk **Projektanta obiektów relacyjnych**.  
  
4.  Ustaw **Pluralizację nazw** do **włączone** = **False** można ustawić [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tak, aby nie zmienia nazwy klasy.  
  
5.  Ustaw **Pluralizację nazw** do **włączone** = **True** do stosowania reguł do określania liczby mnogiej do nazwy klasy obiektów dodanych do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="see-also"></a>Zobacz też  
[LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)