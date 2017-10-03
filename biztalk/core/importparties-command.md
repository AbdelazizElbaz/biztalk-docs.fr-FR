---
title: Commande de ImportParties | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d43e2c-401c-4450-ad9b-2528086b99e4
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15edad97134d3dbccc6f4b1af9395cb0bc01febd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importparties-command"></a>Commande de ImportParties
Importe les contrats et les parties de l’entreprise-entreprise à partir d’un fichier de liaison XML source dans la base de données de configuration, sans importer les artefacts d’application. Pour plus d’informations, consultez **notes** dans cette rubrique.  

> [!IMPORTANT]
> Cette commande est nouvelle, en commençant par  **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** et les versions plus récentes.
  
> [!NOTE]
>  Aucune application n'est spécifiée pour les fichiers de liaison générés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ceux-ci sont donc importés dans l'application par défaut.  
  
## <a name="usage"></a>Utilisation  
  **BTSTask ImportParties-Source**:*valeur* [**- ExcludeEdiFallbackSettings**] [**-Server**:*valeur*] [**-Base de données**:*valeur*]
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis|Valeur|  
|---|---|---|  
|**-Source** | Requis | Le chemin d’accès et le nom du fichier de liaison XML à lire.|
|**-ExcludeEdiFallbackSettings** | Ce paramètre est facultatif | Si spécifié, il exclut les paramètres de (x12 et edifact) de secours edi à partir du fichier de liaison.  |
| **-Serveur** | Ce paramètre est facultatif | Le nom de serveur SQL server hébergeant la base de données de configuration BizTalk. |
| **-Base de données** | Ce paramètre est facultatif | Nom de la base de données de configuration BizTalk. |

## <a name="sample"></a>Exemple
  `BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

## <a name="remarks"></a>Notes
Si le fichier de liaison a également les artefacts de l’application, puis ils ne sont pas importés. Uniquement les parties et les accords sont importés.