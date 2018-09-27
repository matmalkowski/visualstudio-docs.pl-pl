---
title: Zestaw Azure SDK dla języka Python
description: Zestaw Azure SDK dla języka Python ułatwia korzystanie z usług Microsoft Azure z poziomu aplikacji Python działające na dowolnej platformie.
ms.date: 09/56/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 0a68027e975357a404cd7b4f29c837767c60e015
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228815"
---
# <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla języka Python

Zestaw Azure SDK dla języka Python ułatwia wykorzystanie i zarządzanie usługami Microsoft Azure z poziomu aplikacji z systemem Windows, Mac OS x i Linux.

## <a name="installation"></a>Instalacja

Zestaw Azure SDK jest instalowany z [indeksu pakietów języka Python](https://pypi.python.org/pypi/azure).

Zainstaluj **najnowsza stabilna wersja** (obsługuje język Python 2.7 i 3.x) w następujący sposób:

```command
pip install azure
```

Możesz również śledzić [zainstalowania języka Python i zestawu SDK](https://docs.microsoft.com/azure/python-how-to-install/) w dokumentacji platformy Azure.

## <a name="documentation"></a>Dokumentacja

Pełną dokumentację znajduje się na [platforma Azure w Centrum deweloperów języka Python](https://docs.microsoft.com/en-us/python/azure/?view=azure-python). Qucik środowisko pracy, zobacz [wprowadzenie do projektowania aplikacji w chmurze przy użyciu języka Python](/python/azure/python-sdk-azure-get-started?view=azure-python).

Zobacz też tych samouczków dotyczących innych za pomocą usług platformy Azure za pomocą języka Python:

- Usługa Azure App Service:
  - [Tworzenie aplikacji sieci web](/azure/app-service/containers/quickstart-python)
  - [Tworzenie aplikacji internetowej Docker Python i bazy danych PostgreSQL na platformie Azure](/azure/app-service/containers/tutorial-docker-python-postgresql-app)
- Usługa Azure Storage:
  - [Magazyn obiektów blob](/azure/storage/blobs/storage-quickstart-blobs-python)
  - [Table storage i Cosmos DB](/azure/cosmos-db/table-storage-how-to-use-python)
  - [Usługa queue storage](/azure/storage/queues/storage-python-how-to-use-queue-storage)
  - [Flask i Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- Usługa Service Bus
  - [Kolejki usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [Tematy/subskrypcje usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Zarządzanie usługami](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Dla publicznych interfejsów API bez dokumentacji, testy jednostek [repozytorium SDK GitHub](https://github.com/Azure/azure-sdk-for-python) są dobrym źródłem informacji:

- [Magazyn testów jednostkowych](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testy jednostek usługi Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testy jednostkowe management Service](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Obsługa

Repozytorium GitHub dla zestawu SDK znajduje się w [ https://github.com/Azure/azure-sdk-for-python ](https://github.com/Azure/azure-sdk-for-python).

[Plik problemów w repozytorium](https://github.com/Azure/azure-sdk-for-python/issues) Znajdź wszelkie problemy lub pytania dotyczące użycia zestawu SDK.
