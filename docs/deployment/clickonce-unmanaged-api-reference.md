---
title: Dokumentacja interfejsu API niezarządzany ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0651c42abb410b55af956744da7a5e37952770b4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-unmanaged-api-reference"></a>Niezarządzany wykaz interfejsów API ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] niezarządzane publiczne interfejsy API z dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Czyści lub odinstalowuje wszystkie aplikacje online z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pamięci podręcznej aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca wartość HRESULT reprezentujący błąd. W przypadku zarządzanych wyjątkach zwraca 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Uwagi  
 Rozpocznie CleanOnlineAppCache wywoływania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usługi, jeśli nie jest już uruchomiony.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Pobiera informacje na temat wdrażania z manifestu i aktywacji adresu URL.  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|Typ|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Wskaźnik do `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Wskaźnik do `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Wskaźnik do buforu odbierania zerem ciąg znaków określający zwrócona tożsamość pełnej aplikacji.|LPWSTR|  
|`pdwIdentityBufferLength`|Wskaźnik do typu DWORD, który jest długość `pwzApplicationIdentity` buforu w WCHARs. Dotyczy to również miejsce dla znaku zakończenia wartości NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Wskaźnik do buforu odbierania zerem ciąg, który określa architektury procesora wdrożenie aplikacji w manifeście.|LPWSTR|  
|`pdwArchitectureBufferLength`|Wskaźnik do typu DWORD, który jest długość `pwzProcessorArchitecture` buforu w WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Wskaźnik do buforu odbierania zerem ciąg, który określa codebase dla manifest aplikacji w manifeście.|LPWSTR|  
|`pdwCodebaseBufferLength`|Wskaźnik do typu DWORD, który jest długość `pwzApplicationManifestCodebase` buforu w WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Wskaźnik do buforu odbierania ciąg znaków zakończony znakiem NULL, która określa dostawcy rozmieszczenia w manifeście, jeśli jest obecny. W przeciwnym razie zwracany jest pustym ciągiem.|LPWSTR|  
|`pdwProviderBufferLength`|Wskaźnik do typu DWORD, który jest długość `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca wartość HRESULT reprezentujący błąd. Zwraca HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER), jeśli bufor jest za mały.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźniki nie może mieć wartości null. `pcwzActivationUrl` i `pcwzPathToDeploymentManifest` nie może być pusta.  
  
 Odpowiada wywołujący oczyścić adresem URL aktywacji. Na przykład dodawanie specjalne znaków, gdzie są one potrzebne lub usuwanie ciągu zapytania.  
  
 Odpowiada wywołującego limit długości danych wejściowych. Maksymalna długość adresu URL jest na przykład 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Uruchamia lub instaluje aplikację przy użyciu adresu URL wdrożenia.  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|Typ|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Wskaźnik do zerem ciąg, który zawiera adres URL w manifeście rozmieszczenia.|LPCWSTR|  
|`data`|Zarezerwowane do użytku w przyszłości. Musi mieć wartość NULL.|LPVOID —|  
|`flags`|Zarezerwowane do użytku w przyszłości. Musi być równa 0.|DWORD|  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca wartość HRESULT reprezentujący błąd. W przypadku zarządzanych wyjątkach zwraca 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>