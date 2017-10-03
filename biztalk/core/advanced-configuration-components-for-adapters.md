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
# <a name="advanced-configuration-components-for-adapters"></a>Composants de Configuration avancée pour les cartes
L'infrastructure d'adaptateurs BizTalk prend en charge un éditeur déroulant personnalisé, un éditeur de boîtes de dialogue modales personnalisé et un convertisseur de type personnalisé. Ces composants de conception personnalisés sont particulièrement utiles lorsque le nom d'utilisateur et le mot de passe sont utilisés comme informations d'entrée.  
  
 Vous pouvez appeler un éditeur ou un convertisseur de type personnalisé pour un champ de données spécifique (élément ou attribut) du schéma de configuration. Comme décrit dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] aide, l’éditeur doit être dérivé de **System.Drawing.Design.UITypeEditor** et le convertisseur de type à partir de **System.ComponentModel.TypeConverter**.  
  
 Un éditeur remplace le **GetEditStyle** pour spécifier le type de l’éditeur de méthode (**modale** boîte de dialogue, **déroulante** (contrôle), ou **aucun**ci-dessus) et le **EditValue** méthode pour modifier la valeur avec l’éditeur.  
  
 Un convertisseur de type remplace en général le **ConvertFrom**, **CanConvertFrom**, **ConvertTo**, **CanConvertTo**,  **GetStandardValues**, **GetStandardValuesSupported**, et **GetStandardValuesExclusive**méthodes de la bibliothèque de classes .NET Framework.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Concepteur de Configuration d’adaptateur personnalisé](../core/custom-adapter-configuration-designer.md)  
  
-   [Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur](../core/custom-drop-down-editor-for-adapter-configuration.md)  
  
-   [Éditeur de boîte de dialogue modales personnalisé pour la Configuration de l’adaptateur](../core/custom-modal-dialog-editor-for-adapter-configuration.md)  
  
-   [Convertisseur de Type personnalisé pour la Configuration de l’adaptateur](../core/custom-type-converter-for-adapter-configuration.md)