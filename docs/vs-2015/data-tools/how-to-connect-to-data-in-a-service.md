---
title: 'Porady: łączenie z danymi w usłudze | Dokumentacja firmy Microsoft'
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
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 303e41c5d194fbb1c03e35dd37990f8b63dedf4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630364"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Porady: łączenie z danymi w usłudze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: łączenie z danymi w usłudze](https://docs.microsoft.com/visualstudio/data-tools/how-to-connect-to-data-in-a-service).  
  
  
Łączenie aplikacji z danymi zwróconymi z usługi, uruchamiając [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) i wybierając polecenie **usługi** na **wybierz typ źródła danych**strony.  
  
 Po zakończeniu działania kreatora, jest dodawany do projektu odwołanie do usługi i jest natychmiast dostępna w [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Elementy, które pojawiają się w **źródeł danych** okna są zależne od informacji, zwracanemu przez usługę. Niektóre usługi mogą nie dostarczać wystarczających informacji dla **Kreatora konfiguracji źródła danych** do tworzenia obiektów, które można powiązać. Na przykład, jeśli usługa zwraca zestaw danych bez typu, następnie nie widać żadnych elementów w **okna źródeł danych** po ukończeniu kreatora. Jest to spowodowane nietypizowanych zbiorów danych nie zapewniają schematu, dlatego Kreator nie ma wystarczających informacji, aby utworzyć źródło danych.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Aby połączyć aplikację z usługą  
  
1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
2.  Wybierz **usługi** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
3.  Wprowadź adres usługi, o których chcesz używać, lub kliknij przycisk **odnajdź** lokalizowania usług w bieżącym rozwiązaniu, a następnie kliknij przycisk **Przejdź**.  
  
4.  Opcjonalnie, nową **Namespace** można wpisać zamiast wartości domyślne.  
  
    > [!NOTE]
    >  Kliknij przycisk **zaawansowane** otworzyć [skonfigurować usługi odwołania — okno dialogowe](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Kliknij przycisk **OK** można dodać odwołanie do usługi do projektu.  
  
6.  Kliknij przycisk **Zakończ**.  
  
     Źródło danych jest dodawane do **źródeł danych** okna.  
  
## <a name="next-steps"></a>Następne kroki  
  
#### <a name="to-add-functionality-to-your-application"></a>Aby dodać funkcje do aplikacji  
  
-   Wybierz element w **źródeł danych** okna i przeciągnij je na formularz, aby utworzyć formanty powiązane. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

