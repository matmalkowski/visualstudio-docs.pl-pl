---
title: Zestaw Azure SDK for Python | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- azure
ms.openlocfilehash: 647b07e3816551e60e176280199ad5298db53200
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla języka Python

Zestaw Azure SDK for Python ułatwia zużywają i zarządzania usługami Microsoft Azure z aplikacji działających w systemach Windows, Mac OS x i Linux.

## <a name="installation"></a>Instalacja

Zestaw SDK usługi Azure jest instalowany z [indeksu pakietów języka Python](https://pypi.python.org/pypi/azure).

Zainstaluj **najnowsza stabilna wersja** (obsługuje Python 2.7 i 3.3 +) w następujący sposób:

```command
pip install azure
```

Można również wykonać [zainstalować Python i zestawu SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) w dokumentacji platformy Azure.

## <a name="documentation"></a>Dokumentacja

Można znaleźć w dokumentacji [azure sdk dla python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

[Zestawu Azure SDK dla Centrum deweloperów języka Python](http://azure.microsoft.com/develop/python/) również ma liczbę przydatne zasoby, w tym szereg samouczków, takich jak:

- Tworzenie aplikacji sieci web za pomocą [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app), i [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Magazyn obiektów blob](/azure/storage/storage-python-how-to-use-blob-storage)
- [Magazyn tabel](/azure/storage/storage-python-how-to-use-table-storage)
- [Magazyn kolejek](/azure/storage/storage-python-how-to-use-queue-storage)
- [Usługi DocumentDB](/azure/documentdb/documentdb-python-application)
- [Kolejki usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Subskrypcje tematy magistrali usług](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Zarządzanie usługami](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Dla publicznych interfejsach API bez dokumentacji, testów jednostkowych w [repozytorium GitHub zestawu SDK](https://github.com/Azure/azure-sdk-for-python) są dobrym źródłem informacji:

- [Testy jednostkowe magazynu](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testy jednostkowe usługi Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testy jednostkowe usługi zarządzania](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Testy jednostkowe zarządzania zasobów](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Obsługa

Repozytorium Git dla zestawu SDK znajduje się pod adresem [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Plik problemów w repozytorium](https://github.com/Azure/azure-sdk-for-python/issues) znaleźć wszelkie problemy lub pytania dotyczące użycia zestawu SDK.
