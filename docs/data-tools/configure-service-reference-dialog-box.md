---
title: "Odwołanie do usługi — okno dialogowe Konfigurowanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b3b9ae8406845de886009da981eaf7f63e68972b
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
---
# <a name="configure-service-reference-dialog-box"></a>Konfigurowanie odwołania do usługi — Okno dialogowe

**Odwołania do konfigurowania usługi** okno dialogowe umożliwia konfigurowanie zachowania usługi Windows Communication Foundation (WCF).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz polecenie Import i eksport ustawień w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Aby uzyskać dostęp do **skonfigurować odwołania do usługi** okno dialogowe, kliknij prawym przyciskiem myszy usługę odwołania w **Eksploratora rozwiązań** i wybierz polecenie **skonfigurować odwołania do usługi**. Można również otworzyć okno dialogowe, klikając **zaawansowane** przycisk **okno dialogowe Dodaj odwołanie do usługi**.

## <a name="task-list"></a>Lista zadań  
  
-   Aby zmienić adres, gdzie jest hostowana usługa WCF, wprowadź nowy adres w **adres** pola.  
  
-   Aby zmienić poziom dostępu dla klas w klienta WCF, wybierz słowo kluczowe poziom dostępu w **dostępu poziom wygenerowane klasy** listy.  
  
-   Aby wywołać metody usługi WCF asynchronicznie, wybierz **Generuj operacje asynchroniczne** pole wyboru.  
  
-   Aby wygenerować typy kontraktu komunikatu w klienta WCF, wybierz **zawsze Generuj kontraktów komunikatu** pole wyboru.  
  
-   Aby określić listę lub słownik typy kolekcji dla klienta programu WCF, wybierz typy z **— typ kolekcji** i **słownika — typ kolekcji** listy.  
  
-   Aby wyłączyć, typ udostępniania, wyczyść **ponownie użyj typów w przywoływanych zestawach** pole wyboru. Aby włączyć typ udostępniania dla podzbioru zestawów występujących w odwołaniach, wybierz **ponownie użyj typów w przywoływanych zestawach** zaznacz pole wyboru **ponownie użyj typów w określonych przywoływanych zestawach**i wybierz jedną z dostępnych odwołania w **listy zestawy przywoływane**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Adres**  
 Używane do aktualizowania adres sieci Web, w którym wygląda odwołania do usługi dla usługi. Na przykład podczas tworzenia usługi może być hostowana na serwerze projektowym następnie przenieść później na serwerze produkcyjnym wymagających zmiany adresu.  
  
> [!NOTE]
>  Address element jest niedostępne podczas **odwołania do konfigurowania usługi** zostanie wyświetlone okno dialogowe z **okno dialogowe Dodaj odwołanie do usługi**.  
  
 **Poziom dostępu dla wygenerowane klasy**  
 Określa poziom dostępu do kodu dla klasy klienta WCF.  
  
> [!NOTE]
>  W projektach witryny sieci Web, ta opcja jest zawsze równa `Public` i nie można zmienić. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md).  
  
 **Generowanie operacji asynchronicznych**  
 Określa, czy będzie można wywołać metody usługi WCF synchronicznie (ustawienie domyślne) lub asynchronicznie.  
  
 **Generowanie operacji opartego na zadaniach**  
 Podczas pisania kodu asynchroniczne, ta opcja umożliwia korzystanie z zadań równoległych biblioteki (TPL) wprowadzonej z platformą .net 4. Zobacz [zadań Biblioteka równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).  
  
 **Zawsze Generuj kontraktów komunikatu**  
 Określa, czy typy kontraktu komunikatu, zostanie wygenerowany dla klienta programu WCF. Aby uzyskać więcej informacji na temat kontraktów komunikatu, zobacz [za pomocą kontraktów komunikatu](/dotnet/framework/wcf/feature-details/using-message-contracts).  
  
 **Typ kolekcji**  
 Określa typ kolekcji listy dla klienta programu WCF. Jest to domyślny typ <xref:System.Array>.  
  
 **Słownik — typ kolekcji**  
 Określa typ kolekcji słownika dla klienta programu WCF. Jest to domyślny typ <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Ponownie użyj typów w przywoływanych zestawach**  
 Określa, czy klient WCF podejmie próbę ponownego użycia już istnieje w przywoływanych zestawach zamiast generowania nowych typów, gdy usługa jest dodane lub zaktualizowane. Ta opcja jest domyślnie zaznaczona.  
  
 **Ponownie użyj typów w wszystkich przywoływanych zestawach**  
 Po wybraniu wszystkich typów w **listy zestawy przywoływane** zostanie ono użyte ponownie, jeśli to możliwe. Domyślnie ta opcja jest zaznaczona.  
  
 **Ponownie użyj typów w określonych przywoływanych zestawach**  
 W przypadku wybrania tylko wybranych typów w **listy zestawy przywoływane** zostanie ono użyte ponownie.  
  
 **Lista przywoływanych zestawach**  
 Zawiera listę zestawów występujących w odwołaniach projektu lub witryny sieci Web. Gdy **ponownie użyj typów w określonych przywoływanych zestawach** jest zaznaczona, pojedyncze zestawy można zaznaczyć lub wyczyścić.  
  
 **Dodaj odwołanie sieci Web** zostanie wyświetlone okno dialogowe Dodaj odwołanie sieci Web.

> [!NOTE]
> Tej opcji należy używać tylko w przypadku projektów przeznaczonych dla wersji 2.0 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> **Dodaj odwołanie sieci Web** przycisk jest dostępny tylko wtedy, gdy **odwołania do konfigurowania usługi** zostanie wyświetlone okno dialogowe z **okno dialogowe Dodaj odwołanie do usługi**.

## <a name="see-also"></a>Zobacz także

[Porady: Dodawanie odwołania do usługi sieci Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)  
[Usługi Windows Communication Foundation i usługi danych programu WCF](../data-tools/configure-service-reference-dialog-box.md)