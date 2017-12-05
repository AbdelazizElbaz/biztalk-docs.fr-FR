---
title: Comment importer des liaisons pour une Solution EDI-AS2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b918fa2-44f2-4f57-95af-36858cea0d86
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34c25f3837d6eb0c938900b0da9e34246f1c6038
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-import-bindings-for-an-edi-as2-solution"></a>Comment importer des liaisons pour une Solution EDI-AS2
Cette rubrique décrit l'importation de la configuration d'une solution EDI ou AS2 sur un autre ordinateur. Le déploiement d'une solution EDI/AS2 solution est intégré au déploiement d'application BizTalk. Il est accessible via la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'outil de ligne de commande BTSTask.  
  
 Vous pouvez importer la configuration d'un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide d'un fichier de liaison que vous avez créé sur l'ordinateur source en exportant les liaisons appropriées. Pour plus d’informations sur l’exportation d’une configuration dans un fichier de liaison, consultez [comment exporter les liaisons pour une Solution EDI-AS2](../core/how-to-export-bindings-for-an-edi-as2-solution.md). Pour plus d’informations sur un fichier de liaison créé à partir d’une configuration, consultez [Structure d’un fichier de liaison](../core/structure-of-a-binding-file.md).  
  
 Vous pouvez également importer des liaisons dans le cadre de l'importation d'une application à l'aide d'un fichier .msi. Pour plus d’informations, consultez la [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Vous pouvez enfin utiliser la commande BTSTask pour exporter et importer des liaisons. Pour plus d’informations sur BTSTask, consultez la [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md) rubrique dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   Vous devez avoir ajouté une référence à la **Application EDI BizTalk** à partir d’une application BizTalk qui sera utilisée comme une application EDI. Pour obtenir des instructions sur l’ajout d’une référence à l’application EDI BizTalk, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
## <a name="importing-bindings"></a>Importation des liaisons  
 Lorsque vous importez une configuration, les Propriétés EDI existantes sont remplacées. Si vous importez des propriétés pour un tiers du même nom qu'un tiers existant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] remplace les propriétés EDI (ou toute liaison) pour le tiers existant. En outre, si vous importez des propriétés globales EDI, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] remplace les propriétés globales EDI existantes.  
  
 Après avoir importé une configuration, vous devez reconfigurer les mots de passe. Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supprime les mots de passe pour les liaisons du fichier. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Supprime les champs UNB6.1 et UNB6.2 des propriétés EDIFACT et champs ISA1, ISA2, ISA3 et ISA4 de X12 propriétés. Après avoir importé les liaisons, vous devez reconfigurer ces champs sensibles avant de traiter des messages EDI.  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne parvient pas à importer un ensemble de liaisons, cela peut être dû au fait que, dans le fichier de liaison, la propriété Host Trusted diffère de la propriété Authentication Trusted pour l'hôte. Vous pouvez résoudre ce problème en modifiant la propriété Host Trusted dans le fichier de liaison.  
  
> [!NOTE]
>  Importation d’un fichier de liaison à partir de versions précédentes de BizTalk Server dans BizTalk Server peut échouer. Étant donné que le modèle de gestion de partenaire a considérablement changé pour BizTalk Server, l’importation d’un fichier de liaison à partir de versions précédentes de BizTalk Server ne peut pas créer les entités dans BizTalk Server conformément au nouveau modèle. Pour plus d’informations, consultez [comment les définitions de tiers dans le précédent BizTalk Server Versions sont converties en nouvelles entités GPC ?](../core/how-to-import-bindings-for-an-edi-as2-solution.md#BKMK_Party).  
  
### <a name="to-import-the-configuration-from-a-binding-file"></a>Importation de la configuration à partir d'un fichier de liaison  
  
1.  Sur l'ordinateur sur lequel vous voulez importer la configuration, ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Cliquez sur l’Application BizTalk que vous souhaitez importer la configuration EDI/AS2, pointez sur **importer**, puis cliquez sur **liaisons**.  
  
3.  Dans la boîte de dialogue Importer les liaisons, accédez à l’emplacement qui contient votre fichier de liaison, puis cliquez sur **ouvrir**.  
  
4.  Après avoir importé les liaisons, ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Définissez manuellement tous les champs de mot de passe EDI sur les valeurs appropriées.  
  
##  <a name="BKMK_Party"></a>Comment les définitions de tiers dans le précédent BizTalk Server Versions sont converties en nouvelles entités GPC ?  
 Dans BizTalk Server, une définition de tiers est essentiellement un accord qui définit la manière dont les messages sont échangés entre deux partenaires commerciaux. Dans BizTalk Server, EDI et AS2 de messagerie a subi un grand nombre de modifications et le nouveau modèle de gestion des partenaires commerciaux (GPC) requiert désormais des accords à créer entre deux profils d’entreprise commercial. Ainsi, essentiellement, pour qu'un accord existe, vous devez avoir préalablement défini les deux partenaires commerciaux, ainsi que les profils et les paramètres de protocole pour chacun d'eux. Une fois que vous avez défini ces entités, vous pouvez créer un accord de partenariat commercial.  
  
> [!NOTE]
>  Pour plus d’informations relatives aux améliorations du module de plateforme sécurisée dans BizTalk Server, consultez [blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md).  
  
 Étant donné le nouveau modèle d’objet de module de plateforme sécurisée, cela signifie que les applications EDI que vous avez créé dans BizTalk Server ne peut pas être migrées vers BizTalk Server ? La réponse est aucune. Vous pouvez réutiliser les applications existantes à partir de BizTalk Server 2006 R2 ou BizTalk Server 2009 dans BizTalk Server à l’aide de l’outil de Migration de tiers pour migrer les données de tiers à partir de versions précédentes de BizTalk Server. Pour plus d’informations sur l’outil, consultez [migration des artefacts EDI à partir d’une Version précédente de BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
## <a name="see-also"></a>Voir aussi  
 [Importation des liaisons](../core/importing-bindings2.md)