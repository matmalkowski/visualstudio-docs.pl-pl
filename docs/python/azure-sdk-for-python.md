---
title: Zestaw Azure SDK dla języka Python
description: Zestaw Azure SDK dla języka Python ułatwia korzystanie z usług Microsoft Azure z poziomu aplikacji Python działające na dowolnej platformie.
ms.date: 06/26/2018
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
ms.openlocfilehash: 6c7f38dbe58c5172c8480c88ae84c6e28f5d512b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545557"
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

Dokumentację można znaleźć na [azure sdk dla python.readthedocs.org](https://docs.microsoft.com/en-us/python/azure/?view=azure-python).

[Zestawu Azure SDK dla Centrum deweloperów języka Python](https://azure.microsoft.com/develop/python/) zawiera również liczbę przydatne zasoby, w tym liczby samouczków:

- Tworzenie aplikacji sieci web za pomocą [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app), [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app), i [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Magazyn obiektów blob](/azure/storage/storage-python-how-to-use-blob-storage)
- [Magazyn tabel](/azure/storage/storage-python-how-to-use-table-storage)
- [Usługa queue storage](/azure/storage/storage-python-how-to-use-queue-storage)
- [Usługi Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Kolejki usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Tematy/subskrypcje usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Zarządzanie usługami](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Dla publicznych interfejsów API bez dokumentacji, testy jednostek [repozytorium SDK GitHub](https://github.com/Azure/azure-sdk-for-python) są dobrym źródłem informacji:

- [Magazyn testów jednostkowych](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testy jednostek usługi Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testy jednostkowe management Service](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Obsługa

Repozytorium Git dla zestawu SDK znajduje się w [ https://github.com/Azure/azure-sdk-for-python ](https://github.com/Azure/azure-sdk-for-python).

[Plik problemów w repozytorium](https://github.com/Azure/azure-sdk-for-python/issues) Znajdź wszelkie problemy lub pytania dotyczące użycia zestawu SDK.
