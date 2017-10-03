---
title: "Avancée des composants de Configuration pour les adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb31b996-6959-4b5a-9a9f-f48fd91a6180
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8307f54caffec269466dcd9398a9d911fdc83715
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-configuration-components-for-adapters"></a><span data-ttu-id="c032d-102">Composants de Configuration avancée pour les cartes</span><span class="sxs-lookup"><span data-stu-id="c032d-102">Advanced Configuration Components for Adapters</span></span>
<span data-ttu-id="c032d-103">L'infrastructure d'adaptateurs BizTalk prend en charge un éditeur déroulant personnalisé, un éditeur de boîtes de dialogue modales personnalisé et un convertisseur de type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c032d-103">The BizTalk Adapter Framework supports a custom drop-down editor, a custom modal dialog editor, and a custom type converter.</span></span> <span data-ttu-id="c032d-104">Ces composants de conception personnalisés sont particulièrement utiles lorsque le nom d'utilisateur et le mot de passe sont utilisés comme informations d'entrée.</span><span class="sxs-lookup"><span data-stu-id="c032d-104">These custom design components are especially useful when taking user name and password information as input.</span></span>  
  
 <span data-ttu-id="c032d-105">Vous pouvez appeler un éditeur ou un convertisseur de type personnalisé pour un champ de données spécifique (élément ou attribut) du schéma de configuration.</span><span class="sxs-lookup"><span data-stu-id="c032d-105">You can invoke a custom editor or type converter for a specific data field (element or attribute) in the configuration schema.</span></span> <span data-ttu-id="c032d-106">Comme décrit dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] aide, l’éditeur doit être dérivé de **System.Drawing.Design.UITypeEditor** et le convertisseur de type à partir de **System.ComponentModel.TypeConverter**.</span><span class="sxs-lookup"><span data-stu-id="c032d-106">As described in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help, the editor must be derived from **System.Drawing.Design.UITypeEditor** and the type converter from **System.ComponentModel.TypeConverter**.</span></span>  
  
 <span data-ttu-id="c032d-107">Un éditeur remplace le **GetEditStyle** pour spécifier le type de l’éditeur de méthode (**modale** boîte de dialogue, **déroulante** (contrôle), ou **aucun**ci-dessus) et le **EditValue** méthode pour modifier la valeur avec l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="c032d-107">An editor minimally overrides the **GetEditStyle** method to specify the kind of editor (**Modal** dialog, **DropDown** control, or **None** of the above) and the **EditValue** method to change the value with the editor.</span></span>  
  
 <span data-ttu-id="c032d-108">Un convertisseur de type remplace en général le **ConvertFrom**, **CanConvertFrom**, **ConvertTo**, **CanConvertTo**,  **GetStandardValues**, **GetStandardValuesSupported**, et **GetStandardValuesExclusive**méthodes de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c032d-108">A type converter typically overrides the **ConvertFrom**, **CanConvertFrom**, **ConvertTo**, **CanConvertTo**, **GetStandardValues**, **GetStandardValuesSupported**, and **GetStandardValuesExclusive**methods of the .NET Framework Class Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c032d-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c032d-109">In This Section</span></span>  
  
-   [<span data-ttu-id="c032d-110">Concepteur de Configuration d’adaptateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="c032d-110">Custom Adapter Configuration Designer</span></span>](../core/custom-adapter-configuration-designer.md)  
  
-   [<span data-ttu-id="c032d-111">Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="c032d-111">Custom Drop-Down Editor for Adapter Configuration</span></span>](../core/custom-drop-down-editor-for-adapter-configuration.md)  
  
-   [<span data-ttu-id="c032d-112">Éditeur de boîte de dialogue modales personnalisé pour la Configuration de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="c032d-112">Custom Modal Dialog Editor for Adapter Configuration</span></span>](../core/custom-modal-dialog-editor-for-adapter-configuration.md)  
  
-   [<span data-ttu-id="c032d-113">Convertisseur de Type personnalisé pour la Configuration de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="c032d-113">Custom Type Converter for Adapter Configuration</span></span>](../core/custom-type-converter-for-adapter-configuration.md)