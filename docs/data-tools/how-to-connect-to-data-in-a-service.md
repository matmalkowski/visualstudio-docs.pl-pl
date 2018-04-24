---
title: 'Porady: łączenie z danymi w usłudze'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d82e84c8f71b42f5cbe4f6386ed2ceb87b32ffbd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-connect-to-data-in-a-service"></a>Porady: łączenie z danymi w usłudze

Łączenie aplikacji z danymi zwróconymi z usługą, uruchamiając [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png) i wybierając **usługi** na **wybierz typ źródła danych**strony.

Po zakończeniu działania kreatora, odwołania do usługi zostanie dodany do projektu i jest dostępny w [Data Sources — okno](add-new-data-sources.md).

> [!NOTE]
> Elementy, które są widoczne w **źródeł danych** okna są zależne od informacje zwracane usługi. Niektóre usługi mogą nie zawiera informacji wystarczających **Kreator konfiguracji źródła danych** do tworzenia obiektów powiązania. Na przykład, jeśli usługa zwraca nietypizowanego zestawu danych, następnie nie widać żadnych elementów w **Data Sources — okno** po ukończeniu kreatora. Jest to spowodowane nietypizowane zbiory danych nie udostępniają schematu, więc kreator nie ma wystarczających informacji do utworzenia źródła danych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Aby połączyć aplikację z usługą

1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.

2.  Wybierz **usługi** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

3.  Wprowadź adres usługi ma zostać użyty, lub kliknij przycisk **odnajdowania** znajdowanie usług w bieżącym rozwiązaniu, a następnie kliknij przycisk **Przejdź**.

4.  Opcjonalnie, nowe **Namespace** można wpisać zamiast wartości domyślnej.

    > [!NOTE]
    > Kliknij przycisk **zaawansowane** otworzyć [skonfigurować usługi odwołania — okno dialogowe](../data-tools/configure-service-reference-dialog-box.md).

5.  Kliknij przycisk **OK** można dodać odwołania do usługi do projektu.

6.  Kliknij przycisk **Zakończ**.

     Źródło danych jest dodawane do **źródeł danych** okna.

## <a name="next-steps"></a>Następne kroki

Dodawanie funkcji do aplikacji, wybierz element w **źródeł danych** okna i przeciągnij go na formularz, aby utworzyć formanty powiązane. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Powiązywanie kontrolek WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Usługi Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)