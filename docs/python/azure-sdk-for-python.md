---
title: Zestaw Azure SDK dla języka Python
description: Zestaw Azure SDK for Python można łatwo korzystać z usług Microsoft Azure z Python aplikacji działających na dowolnej platformie.
ms.custom: ''
ms.date: 01/22/2018
ms.technology:
- devlang-python
dev_langs:
- python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 56ccd85dd5dfd9ce6f82a68ef18df303631987b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla języka Python

Zestaw Azure SDK for Python ułatwia zużywają i zarządzania usługami Microsoft Azure z aplikacji działających w systemach Windows, Mac OS x i Linux.

## <a name="installation"></a>Instalacja

Zestaw SDK usługi Azure jest instalowany z [indeksu pakietów języka Python](https://pypi.python.org/pypi/azure).

Zainstaluj **najnowsza stabilna wersja** (obsługuje Python 2.7 i 3.x) w następujący sposób:

```command
pip install azure
```

Można również wykonać [zainstalować Python i zestawu SDK](https://docs.microsoft.com/azure/python-how-to-install/) w dokumentacji platformy Azure.

## <a name="documentation"></a>Dokumentacja

Można znaleźć w dokumentacji [azure sdk dla python.readthedocs.org](https://docs.microsoft.com/en-us/python/azure/?view=azure-python).

[Zestawu Azure SDK dla Centrum deweloperów języka Python](http://azure.microsoft.com/develop/python/) również ma wiele przydatnych zasobów, w tym liczby samouczki:

- Tworzenie aplikacji sieci web za pomocą [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app), i [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Magazyn obiektów blob](/azure/storage/storage-python-how-to-use-blob-storage)
- [Magazyn tabel](/azure/storage/storage-python-how-to-use-table-storage)
- [Magazyn kolejek](/azure/storage/storage-python-how-to-use-queue-storage)
- [Bazy danych Azure rozwiązania Cosmos](/azure/cosmos-db/sql-api-python-application)
- [Kolejki usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Subskrypcje tematy magistrali usług](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Zarządzanie usługami](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Dla publicznych interfejsach API bez dokumentacji, testów jednostkowych w [repozytorium GitHub zestawu SDK](https://github.com/Azure/azure-sdk-for-python) są dobrym źródłem informacji:

- [Testy jednostkowe magazynu](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testy jednostkowe usługi Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testy jednostkowe usługi zarządzania](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Testy jednostkowe zarządzania zasobów](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Obsługa

Repozytorium Git dla zestawu SDK znajduje się pod adresem [ https://github.com/Azure/azure-sdk-for-python ](https://github.com/Azure/azure-sdk-for-python).

[Plik problemów w repozytorium](https://github.com/Azure/azure-sdk-for-python/issues) znaleźć wszelkie problemy lub pytania dotyczące użycia zestawu SDK.
