---
title: 'Porady: dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9e39b28a3de5aa97ac7c0673cd16b71508ae4276
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Porady: dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF
A *usługi odwołanie* umożliwia projektu do dostępu do co najmniej jeden [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Użyj **Dodaj odwołanie do usługi** okno dialogowe, aby wyszukać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w bieżącym rozwiązaniu lokalnie, w sieci lokalnej lub w Internecie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-a-service-reference"></a>Dodawanie odwołania do usługi

#### <a name="to-add-a-reference-to-an-external-service"></a>Aby dodać odwołanie do zewnętrznej usługi

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, który chcesz dodać usługę, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.

     **Dodaj odwołanie do usługi** zostanie wyświetlone okno dialogowe.

2.  W **adres** , wprowadź adres URL dla usługi, a następnie kliknij **Przejdź** wyszukiwania dla usługi. Gdy usługa implementuje zabezpieczeń nazwę i hasło użytkownika, może pojawić się prośba o nazwę użytkownika i hasło.

    > [!NOTE]
    >  Użytkownik powinien odwoływać się tylko usługi z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

     Możesz też wybrać adres URL z **adres** listę, która przechowuje poprzednie 15 adresów URL, w których znaleziono prawidłową usługę metadanych.

     Pasek postępu jest wyświetlana podczas wyszukiwania. Można zatrzymać wyszukiwania w dowolnym momencie, klikając **zatrzymać**.

3.  W **usług** listy, rozwiń węzeł usługi, który chcesz użyć, a następnie wybierz zestaw jednostek.

4.  W **Namespace** wprowadź obszar nazw, który ma być używany dla odwołania.

5.  Kliknij przycisk **OK** można dodać odwołania do projektu.

     Klient usługi (proxy) jest generowany, a metadane opisujące usługi są dodawane do pliku app.config.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Aby dodać odwołanie do usługi w bieżącym rozwiązaniu

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, który chcesz dodać usługę, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.

     **Dodaj odwołanie do usługi** zostanie wyświetlone okno dialogowe.

2.  Kliknij przycisk **odnajdywanie**.

     Wszystkie usługi (zarówno [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do **usług** listy.

3.  W **usług** listy, rozwiń węzeł usługi, który chcesz użyć, a następnie wybierz zestaw jednostek.

4.  W **Namespace** wprowadź obszar nazw, który ma być używany dla odwołania.

5.  Kliknij przycisk **OK** można dodać odwołania do projektu.

     Klient usługi (proxy) jest generowany, a metadane opisujące usługi są dodawane do pliku app.config.

## <a name="updating-a-service-reference"></a>Aktualizacja odwołania do usługi
 Modelu danych jednostki dla [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] czasami ulegnie zmianie. W takim przypadku należy zaktualizować odwołania do usługi.

#### <a name="to-update-a-service-reference"></a>Aby zaktualizować odwołania do usługi

-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy odwołania do usługi, a następnie kliknij przycisk **odwołania do usługi aktualizacji**.

     Okno dialogowe postępu jest wyświetlana, gdy odwołanie jest aktualizowane z oryginalnej lokalizacji, a klienta usługi jest generowany ponownie, aby odzwierciedlały zmiany w metadanych.

## <a name="removing-a-service-reference"></a>Usuwanie odwołań usługi
 Jeśli to odwołanie do usługi jest już używana, można go usunąć z rozwiązania.

#### <a name="to-remove-a-service-reference"></a>Aby usunąć odwołania do usługi

-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy odwołania do usługi, a następnie kliknij przycisk **usunąć**.

     Klient usługi zostanie usunięty z rozwiązania, a metadane opisujące usługi zostaną usunięte z pliku app.config.

    > [!NOTE]
    >  Każdy kod odwołujący się do odwołania do usługi będą musiały zostać usunięte ręcznie.

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)