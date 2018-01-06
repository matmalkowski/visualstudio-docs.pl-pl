---
title: "Porady: wykluczanie projektów z kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8392a17a1d1f0648176c6b68463102e31c61cf20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exclude-projects-from-a-build"></a>Poradnik: Wykluczanie projektów z kompilacji
Można tworzyć rozwiązania bez tworzenia wszystkie projekty, które zawiera. Może na przykład wykluczyć projektu, który dzieli kompilacji. Można następnie zbudować projekt po możesz zbadać i adres problemy.  
  
 Projekt można wykluczyć, wykonując następujących metod:  
  
-   Usunięcie go tymczasowo z aktywnej konfiguracji rozwiązania.  
  
-   Tworzenie konfiguracji rozwiązania, która nie zawiera projektu.  
  
 Aby uzyskać więcej informacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Aby tymczasowo usunąć projekt z aktywnej konfiguracji rozwiązania  
  
1.  Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**.  
  
2.  W **projektu kontekstów** tabeli, Znajdź projektu, które chcesz wykluczyć z kompilacji.  
  
3.  W **kompilacji** kolumny dla projektu, usuń zaznaczenie pola wyboru.  
  
4.  Wybierz **Zamknij** przycisk, a następnie ponownie skompiluj rozwiązanie.  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Aby utworzyć konfigurację rozwiązania, która nie obejmuje projektu  
  
1.  Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**.  
  
2.  W **aktywnej konfiguracji rozwiązania** wybierz  **\<nowy >**.  
  
3.  W **nazwa** wprowadź nazwę dla konfiguracji rozwiązania.  
  
4.  W **Kopiuj ustawienia** wybierz konfigurację rozwiązania, na którym chcesz utworzyć nową konfigurację (na przykład **debugowania**), a następnie wybierz pozycję **OK** przycisku .  
  
5.  W **programu Configuration Manager** okno dialogowe, wyczyść pole wyboru w **kompilacji** kolumny dla projektu, który chcesz wykluczyć, a następnie wybierz pozycję **Zamknij** przycisku.  
  
6.  Na **standardowe** narzędzi, sprawdź, czy nowa konfiguracja rozwiązania jest aktywna konfiguracja w **konfiguracje rozwiązania** pole.  
  
7.  Na pasku menu wybierz **kompilacji**, **Kompiluj ponownie rozwiązanie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)   
 [Porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md)   
 [Instrukcje: Równoczesne kompilowanie wielu konfiguracji](../ide/how-to-build-multiple-configurations-simultaneously.md)