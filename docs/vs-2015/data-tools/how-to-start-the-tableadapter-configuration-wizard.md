---
title: 'Porady: uruchom Kreator konfiguracji TableAdapter | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0cf7d3e5ace98ac73f97909b184ce04b86d4b9ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678596"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Porady: Uruchom Kreator konfiguracji TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Kreator konfiguracji TableAdapter** pozwala tworzyć i edytować TableAdapters w silnie typizowanych elementów DataSet. Kreator utworzy TableAdapters na podstawie instrukcji języka SQL, które możesz wprowadzić w kreatorze lub istniejących procedur składowanych w bazie danych. Kreatora można również utworzyć nowe procedury składowane w bazie danych, w oparciu o instrukcji SQL, które możesz wprowadzić w kreatorze.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Aby uruchomić Kreatora konfiguracji TableAdapter, aby utworzyć nowy obiekt TableAdapter  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Jeśli nie masz zestaw danych w projekcie, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Jeśli tworzysz nowy obiekt TableAdapter, przeciągnij **TableAdapter** obiektu z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.  
  
3.  Na **wybierz połączenie danych** stronie, wybierz połączenie danych z listy dostępnych połączeń lub **nowe połączenie** do utworzenia nowego połączenia.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>Aby uruchomić Kreatora konfiguracji TableAdapter, aby edytować istniejące TableAdapter  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Kliknij prawym przyciskiem myszy obiekt TableAdapter w **Projektanta obiektów Dataset** i wybierz polecenie **Konfiguruj**. W kreatorze jest otwierany **Generuj instrukcje SQL** strony lub **powiązać polecenia do istniejących procedur składowanych** strony, w zależności od tego, jak został pierwotnie skonfigurowane TableAdapter.  
  
3.  Ukończ pracę kreatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Porady: Tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy Windows Forms](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)