---
title: "Porady: łączenie z danymi w usłudze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 58d22a756edd625a9c664862d05de5fe405fd9f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-connect-to-data-in-a-service"></a>Porady: łączenie z danymi w usłudze
Łączenie aplikacji z danymi zwróconymi z usługą, uruchamiając [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png) i wybierając **usługi** na **wybierz typ źródła danych**strony.  
  
 Po zakończeniu działania kreatora, odwołania do usługi zostanie dodany do projektu i jest dostępny w [Data Sources — okno](add-new-data-sources.md).  
  
> [!NOTE]
>  Elementy, które są widoczne w **źródeł danych** okna są zależne od informacje zwracane usługi. Niektóre usługi mogą nie zawiera informacji wystarczających **Kreator konfiguracji źródła danych** do tworzenia obiektów powiązania. Na przykład, jeśli usługa zwraca nietypizowanego zestawu danych, następnie nie widać żadnych elementów w **Data Sources — okno** po ukończeniu kreatora. Jest to spowodowane nietypizowane zbiory danych nie udostępniają schematu, więc kreator nie ma wystarczających informacji do utworzenia źródła danych.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Aby połączyć aplikację z usługą  
  
1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
2.  Wybierz **usługi** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.  
  
3.  Wprowadź adres usługi ma zostać użyty, lub kliknij przycisk **odnajdowania** znajdowanie usług w bieżącym rozwiązaniu, a następnie kliknij przycisk **Przejdź**.  
  
4.  Opcjonalnie, nowe **Namespace** można wpisać zamiast wartości domyślnej.  
  
    > [!NOTE]
    >  Kliknij przycisk **zaawansowane** otworzyć [skonfigurować usługi odwołania — okno dialogowe](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Kliknij przycisk **OK** można dodać odwołania do usługi do projektu.  
  
6.  Kliknij przycisk **Zakończ**.  
  
     Źródło danych jest dodawane do **źródeł danych** okna.  
  
## <a name="next-steps"></a>Następne kroki  
  
#### <a name="to-add-functionality-to-your-application"></a>Dodawanie funkcji do aplikacji  
  
-   Wybierz element w **źródeł danych** okna i przeciągnij go na formularz, aby utworzyć formanty powiązane. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie formantów WPF z usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Usługi Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)