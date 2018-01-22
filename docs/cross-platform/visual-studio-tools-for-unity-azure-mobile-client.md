---
title: "Visual Studio Tools for Unity klienta usługi Azure Mobile wskazówki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: f6b7861b1cf027e4c2f47f711d6f47376dec3a7c
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="implement-the-azure-mobileserviceclient"></a>Implementowanie Azure MobileServiceClient

Jest centralnej do zestawu SDK klienta usługi Azure Mobile <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a>, co umożliwia dostęp do zaplecza aplikacji mobilnej.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Znajdź adres URL zaplecza aplikacji mobilnej

`MobileServiceClient` Konstruktor pobiera adres URL aplikacji mobilnej jako parametru, więc przed idąc dalej, Znajdź adres URL.

1. W portalu Azure kliknij **usługi aplikacji** przycisku.

    ![Kliknij opcję usługi aplikacji](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Kliknij pozycję aplikacji mobilnej.

    ![Kliknij przycisk aplikacji mobilnej](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Skopiuj adres URL zaplecza aplikacji mobilnej.

    ![Skopiuj adres URL](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Tworzenie pojedynczych MobileServiceClient

Powinny istnieć tylko jedno wystąpienie `MobileServiceClient`, więc przewodniku zastosowano zmiany wzorca singleton.

1. Wewnątrz **zasoby/skrypty** katalogu projektu Unity, Utwórz nowy skrypt języka C# o nazwie **AzureMobileServiceClient**.

2. Otwórz `AzureMobileServiceClient` skryptów i usunąć istniejący kod szablonu, w tym za pomocą instrukcji i deklaracji klasy.

3. Dodaj następujący kod:

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Jeśli IntelliSense nie rozpoznaje Microsoft.WindowsAzure przestrzeni nazw, sprawdź, czy po wykonaniu wszystkich czynności [przygotować środowisko projektowe](visual-studio-tools-for-unity-azure-prepare.md) sekcji.

4. W powyższym kodzie Zamień `MOBILE_APP_URL` z adresem URL zaplecza aplikacji mobilnej.

## <a name="next-step"></a>Następny krok

* [Aktualizacja Unity Mono zabezpieczeń magazynu](visual-studio-tools-for-unity-azure-security.md)
