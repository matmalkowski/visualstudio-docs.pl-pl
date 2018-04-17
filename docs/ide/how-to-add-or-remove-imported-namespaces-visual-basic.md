---
title: 'Porady: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70cffeb24c8eb13823b381b7cc5d0c2034a57b80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Porady: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)
Importowanie przestrzeni nazw umożliwia przy użyciu elementów z tej przestrzeni nazw w kodzie bez pełni kwalifikujących się elementu. Na przykład, jeśli chcesz, aby uzyskać dostęp do `Create` metody w `System.Messaging.MessageQueue` klasy, można zaimportować `System.Messaging` przestrzeni nazw i po prostu odwoływać się do elementu, należy w kodzie jako `MessageQueue.Create`.  

 Importowane przestrzenie nazw są zarządzane na **odwołania** strony **projektanta projektu**. Importy określić w tym oknie dialogowym są przekazywane bezpośrednio do kompilatora (*/importuje*) i dotyczą wszystkich plików w projekcie. Użyj `Imports` instrukcję, aby korzystać z obszaru nazw w pliku kodu jednego źródła.  

### <a name="to-add-an-imported-namespace"></a>Aby dodać zaimportowaną przestrzenią nazw  

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzła projektu.  

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.  

3.  W **importowane przestrzenie nazw** listy, zaznacz pole wyboru dla przestrzeni nazw, które chcesz dodać.  

    > [!NOTE]
    >  Aby można było zaimportować, przestrzeni nazw musi być w składnika. Przestrzeń nazw nie ma na liście, należy dodać odwołanie do składnika, który go zawiera. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md).  
  
### <a name="to-remove-an-imported-namespace"></a>Aby usunąć zaimportowaną przestrzenią nazw  

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzła projektu.  

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.  

3.  W **importowane przestrzenie nazw** listy, wyczyść pole wyboru dla przestrzeni nazw, który chcesz usunąć.  

## <a name="user-imports"></a>Importy użytkownika  
 Importy użytkownika można importować określonej klasy w przestrzeni nazw, a nie cały obszar nazw. Na przykład aplikacja może być importu dla <xref:System.Diagnostics> przestrzeni nazw, ale tylko klasy w tej przestrzeni nazw, która planuje się `Debug` klasy. Można zdefiniować <xref:System.Diagnostics.Debug> jako użytkownik zaimportować, a następnie usuń importu dla <xref:System.Diagnostics>.  

 Jeśli później zmienić należy uwzględnić i zdecydować, że jego naprawdę `EventLog` klasy, która jest potrzebna, można wprowadzić <xref:System.Diagnostics.EventLog> jako użytkownik Importuj i Zastąp <xref:System.Diagnostics.Debug> przy użyciu funkcji aktualizacji.  

### <a name="to-add-a-user-import"></a>Aby dodać importu użytkownika  

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzła projektu.  

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.  

3.  W polu tekstowym poniżej **importowane przestrzenie nazw** listy, wpisz pełną nazwę przestrzeni nazw, które chcesz zaimportować, włącznie z przestrzenią nazw głównych.  

4.  Kliknij przycisk **dodać importu użytkownika** przycisk, aby dodać obszar nazw jako **importowane przestrzenie nazw** listy.  

    > [!NOTE]
    >  **Dodać importu użytkownika** przycisk zostanie wyłączona, jeśli przestrzeń nazw pasujący już na liście; nie można dodać importu dwa razy.  

### <a name="to-update-a-user-import"></a>Aby zaktualizować importu użytkownika  

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** węzła projektu.  

2.  W **projektanta projektu**, kliknij przycisk **odwołania** kartę.  

3.  W **importowane przestrzenie nazw** listy, wybierz obszar nazw, które chcesz zmienić.  

4.  W polu tekstowym poniżej **importowane przestrzenie nazw** listy, wprowadź nazwę dla nowej przestrzeni nazw.  

5.  Kliknij przycisk **zaktualizować importu użytkownika** przycisk, aby zaktualizować obszar nazw w **importowane przestrzenie nazw** listy.  

## <a name="see-also"></a>Zobacz także  
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
