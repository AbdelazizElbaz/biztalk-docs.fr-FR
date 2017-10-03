---
title: Commande de ExportParties | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b421c8ed-d505-48ba-9d1d-8519c9d51750
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca525872ccc1cd941673189c4ac176fc4631f22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exportparties-command"></a>Commande de ExportParties
Exporte toutes les parties et les contrats à un fichier de liaison XML.

> [!IMPORTANT]
> Cette commande est nouvelle, en commençant par  **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** et les versions plus récentes.

## <a name="usage"></a>Utilisation
  **BTSTask ExportParties-Destination**:*valeur* [**-Server**:*valeur*] [**-base de données**: *valeur*]
  
## <a name="parameters"></a>Paramètres

|Paramètre|Requis|Valeur|  
|---|---|---|  
| **-Destination** | Requis | Chemin d’accès et le nom du fichier de liaison XML à écrire. |
| **-Serveur** | Ce paramètre est facultatif | Le nom de serveur SQL server hébergeant la base de données de configuration BizTalk. |
| **-Base de données** | Ce paramètre est facultatif | Nom de la base de données de configuration BizTalk.|

## <a name="sample"></a>Exemple
  `ExportParties  -Destination:"C:\Temp\MyParties.Xml"` 

## <a name="remarks"></a>Notes
  Uniquement les parties, les contrats et les paramètres de secours EDI sont exportés. Aucun artefact d’application n’est exportés.
