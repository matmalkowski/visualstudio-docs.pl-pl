---
title: IManagedAddin — interfejs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f29356a3e11634d742d6f6022c35cf8f10871eec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddin-interface"></a>IManagedAddin — interfejs
  Implementowanie interfejsu imanagedaddin — można utworzyć składnika, który ładuje zarządzanych dodatków VSTO. Ten interfejs został dodany w Microsoft Office system 2007.  
  
## <a name="syntax"></a>Składnia  
  
```c++
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli wymieniono metody, które są zdefiniowane przez imanagedaddin — interfejs.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wywoływane, gdy Microsoft Office ładowania aplikacji zarządzanych dodatku VSTO.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wywoływana tuż przed Microsoft Office aplikacji zwalnia zarządzane dodatku VSTO.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacje Microsoft Office, począwszy od pakietu Microsoft Office 2007 umożliwia imanagedaddin — interfejs ułatwić obciążenia dodatków VSTO pakietu Office. Można zaimplementować imanagedaddin — interfejs do tworzenia własnych dodatku VSTO modułu ładującego i środowiska wykonawczego dla zarządzanych VSTO dodatki, zamiast modułu ładującego dodatku VSTO (*VSTOLoader.dll*) i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Aby uzyskać więcej informacji, zobacz [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>W jaki sposób zarządzane dodatki są ładowane  
 Podczas uruchamiania aplikacji, wykonywane są następujące kroki:  
  
1.  Aplikacja odnajduje dodatków VSTO się wpisy w następującym kluczu rejestru:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Nazwa aplikacji >_ \Addins\**  
  
     Każdy wpis w tym kluczu rejestru jest unikatowy identyfikator dodatku VSTO. Zazwyczaj jest to nazwa zestawu dodatku VSTO.  
  
2.  Aplikacja szuka `Manifest` wpis w wpis dla każdego dodatku VSTO.  
  
     Zarządzane dodatków VSTO może przechowywać pełną ścieżkę manifestu w `Manifest` wpis w **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Nazwa aplikacji >_ \Addins\\  _\<identyfikator dodatku >_**. Manifestu to plik (zazwyczaj plik XML), który zawiera informacje, które umożliwiają załadowanie dodatku VSTO.  
  
3.  Jeśli aplikacja znajdzie `Manifest` wpisu, aplikacja próbuje załadować zarządzanego dodatku VSTO modułu ładującego składnika. Aplikacja wykonuje to zadanie w trakcie tworzenia obiektu COM, który implementuje interfejs imanagedaddin —.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zawiera składnik dodatku VSTO modułu ładującego (*VSTOLoader.dll*), lub utworzyć własne przez wdrożenie imanagedaddin — interfejs.  
  
4.  Wywołania aplikacji [IManagedAddin::Load](../vsto/imanagedaddin-load.md) — metoda i przekazuje wartości `Manifest` wpisu.  
  
5.  [IManagedAddin::Load](../vsto/imanagedaddin-load.md) metoda wykonuje zadania wymagane do załadowania dodatku VSTO, takich jak Konfigurowanie zasad domeny i zabezpieczeń aplikacji dodatku VSTO, który jest ładowany.  
  
 Aby uzyskać więcej informacji na temat rejestru klucze używających aplikacji Microsoft Office, aby odnaleźć i załadować zarządzane dodatków VSTO, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-to-implement-imanagedaddin"></a>Wskazówki dotyczące implementacji imanagedaddin —  
 Imanagedaddin — w przypadku zastosowania, konieczna jest rejestracja biblioteki DLL zawierającej wdrożenia za pomocą następującego identyfikatora CLSID:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Aplikacje Microsoft Office Użyj tego identyfikatora CLSID, aby utworzyć obiekt COM, który implementuje imanagedaddin —.  
  
> [!CAUTION]  
>  Ten identyfikator CLSID jest już używana przez *VSTOLoader.dll* w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. W związku z tym, jeśli używasz imanagedaddin — do tworzenia własnego modułu ładującego dodatku VSTO i składnika środowiska wykonawczego, nie można wdrożyć składnika na komputerach z systemem dodatków VSTO, które opierają się na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Zobacz także  
 [Niezarządzany wykaz interfejsów API &#40;programowanie Office w Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  