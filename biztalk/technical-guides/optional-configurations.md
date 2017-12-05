---
title: Configurations facultatives | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f4b0b51-2cad-4cb5-b6cd-4db92bd199fa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b19646c9c83eff4a3171b4d25763a6b581d45b1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="optional-configurations"></a>Configurations facultatives
Après avoir importé le Pack d’administration de BizTalk Server, le volet de navigation du volet surveillance affiche les types d’objets qui sont détectés automatiquement. Pour obtenir la liste des types d’objets, consultez [objets du Pack d’administration détecte](../technical-guides/objects-the-management-pack-discovers.md) section. Vous pouvez modifier la configuration de la détection par défaut des objets découverts par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration. La fonctionnalité de remplacements d’Operations Manager 2007 R2/2012 vous permet de modifier les paramètres de configuration.  
  
 Pour un type d’objet qui n’est pas découvert automatiquement, vous pouvez activer le paramètre de détection automatique dans le **création** volet dans la Console opérateur.  
  
#### <a name="to-use-an-override-to-change-the-setting-for-automatic-discovery"></a>Pour utiliser un remplacement pour modifier le paramètre de détection automatique  
  
1.  Dans le volet Création, développez **objets du Pack d’administration**, puis cliquez sur **détections**.  
  
2.  Dans la barre d’outils Operations Manager, cliquez sur **étendue**, filtrez les objets qui apparaissent dans le volet de détails à inclure uniquement les objets BizTalk Server.  
  
3.  Dans le volet de détails, cliquez sur le type d’objet que vous souhaitez modifier le paramétrage.  
  
4.  Dans la barre d’outils Operations Manager, cliquez sur **substitue**, cliquez sur **remplacer la détection d’objets**, puis cliquez sur **pour tous les objets de type :** \<  *nom du type d’objet*\>, **pour un groupe, pour un objet spécifique de type :** \< *nom du type d’objet*\>, ou  **Pour tous les objets d’un autre type**.  
  
5.  Dans le **propriétés du remplacement** boîte de dialogue, cliquez sur le **remplacer** zone pour le **activé** paramètre que vous souhaitez modifier.  
  
6.  Sous **Pack d’administration**, cliquez sur **nouveau** à créer une version non scellée du Pack d’administration, puis cliquez sur **OK**.  
  
 Après avoir modifié le paramètre de remplacement, le type d’objet sera automatiquement détecté et apparaîtra dans le volet analyse sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour plus d’informations sur la définition des remplacements, consultez [remplacements dans Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=86870) (http://go.microsoft.com/fwlink/?LinkId=86870).