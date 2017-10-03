---
title: Comment exporter des liaisons pour une Solution EDI AS2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 856ab630-66c4-4496-884a-fdbe641143c5
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aceeb81933324d5b3c164396290fe7b99cdc7295
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-an-edi-as2-solution"></a>Comment exporter des liaisons pour une Solution EDI AS2
Cette rubrique décrit l'exportation de la configuration depuis un ordinateur configuré comme une solution EDI et/ou AS2. Cela vous permet de définir la même configuration sur un autre ordinateur de manière automatisée. Vous pouvez exporter les liaisons à partir d'une application, d'un groupe ou d'un assembly.  
  
 Vous créez un fichier de liaison à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le fichier de liaison .xml contient toutes les informations pertinentes pour votre configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela inclut toutes les propriétés de configuration EDI et AS2, à l'exception de certaines informations de sécurité. Pour plus d’informations sur les nœuds dans un fichier de liaison (y compris des nœuds EDI et AS2), consultez [Structure d’un fichier de liaison](../core/structure-of-a-binding-file.md). Pour obtenir des informations générales sur les liaisons EDI/AS2, consultez « Nœuds EDI et AS2 dans le fichier de liaison [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] » ci-après.  
  
 Vous pouvez également exporter des liaisons dans le cadre de l'exportation d'une application à l'aide d'un fichier .msi. Pour plus d’informations, consultez la [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md). Vous pouvez enfin utiliser la commande BTSTask pour exporter et importer des liaisons. Pour plus d’informations sur BTSTask, consultez [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md).  
  
 **L’exportation des liaisons**  
  
 Lorsque vous exportez la configuration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exporte automatiquement les propriétés EDI et autres informations sur tous les tiers liés. Si vous activez l'exportation des informations de tiers global, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exporte également les propriétés pour les tiers qui ne sont pas liés à une orchestration et les propriétés globales EDI. Vous pouvez exporter les informations de tiers global de trois manières :  
  
-   En activant la propriété Exporter les informations du tiers global dans la boîte de dialogue Exporter les liaisons.  
  
-   En activant la case à cocher Tiers globaux dans le volet Sélectionner les ressources de l'Assistant Exportation de fichier MSI.  
  
-   En utilisant le commutateur GlobalParties dans l'outil de ligne de commande BTSTask, comme suit :  
  
    ```  
    BTSTask ExportBindings -Destination:value ((([-ApplicationName:value] | [-AssemblyName:value]) [-GlobalParties]) | [-GroupLevel])  
    ```  
  
 Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supprime les mots de passe pour les liaisons du fichier. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Supprime les champs UNB6.1 et UNB6.2 des propriétés EDIFACT et champs ISA1, ISA2, ISA3 et ISA4 de X12 propriétés.  
  
 Outre l'utilisation de la commande export-bindings, export-application ou BTSTask, vous pouvez créer un fichier de liaison XML manuellement. En procédant ainsi, vous pouvez exporter les paramètres de tiers et EDI à partir d'une application sectorielle. Vous pouvez ensuite importer les liaisons à l'aide de la commande import-bindings ou de la commande BTSTask.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d'informations, consultez « Autorisations nécessaires au déploiement et à la gestion d'une application BizTalk » dans la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="exporting-the-configuration-into-a-binding-file"></a>Exportation de la configuration dans un fichier de liaison  
  
1.  Sur l'ordinateur à partir duquel vous voulez exporter la configuration, ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Cliquez sur l’Application BizTalk que vous souhaitez copier la configuration à partir de, pointez sur **exporter**, puis cliquez sur **liaisons**.  
  
    > [!NOTE]
    >  Vous pouvez également utiliser l'utilitaire BTSTask pour exporter ou importer la configuration.  
  
3.  Sélectionnez l'option export, en choisissant d'exporter à partir de l'application ou du groupe actuel ou en exportant des liaisons pour un assembly.  
  
4.  Si vous voulez exporter toutes les parties et leurs propriétés non sensibles, même si une orchestration n’est pas liée à ceux-ci, cliquez sur **informations d’exportation de tiers Global**.  
  
    > [!NOTE]
    >  Si vous ne cliquez pas sur **informations d’exportation de tiers Global**, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exporter les propriétés pour toutes les parties qui sont liés à une orchestration, dans le fichier de liaison. Toutefois, il n’exporte pas les tiers qui ne sont pas liés à une orchestration, sauf si vous cliquez sur **informations d’exportation de tiers Global**.  
  
    > [!NOTE]
    >  Le fichier de liaison généré pendant la **informations d’exportation de tiers Global** propriété est sélectionnée inclut la configuration de toutes les parties définies sur l’ordinateur. Il n'est pas possible d'exporter la configuration d'un sous-ensemble de l'ensemble complet de tiers défini sur un ordinateur.  
  
5.  Cliquez sur **OK** exporter les liaisons.  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'exporte pas de champs EDI sensibles, tels que les mots de passe ou les informations de sécurité / d'authentification. Il exporte une chaîne vide pour tout champ EDI sensible. Après avoir importé les liaisons sur un autre ordinateur, vous devez définir manuellement les valeurs des champs EDI sensibles.  
  
6.  Notez manuellement les champs EDI sensibles, tels que les mots de passe ou les informations de sécurité / d'authentification, pour un paramétrage ultérieur sur l'ordinateur sur lequel vous importez les liaisons.  
  
## <a name="edi-and-as2-nodes-in-the-biztalk-server-binding-file"></a>Nœuds EDI et AS2 dans le fichier de liaison BizTalk Server  
 Si vous exportez votre configuration avec la **informations d’exportation de tiers Global** activée [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère un fichier de liaison qui a les nœuds suivants :  
  
```  
EdiData  
   PartyEDIProperties  
      PartnerAgreement  
         Contacts  
      PartnerEdifact  
         PartnerEdifactReceiverGroups  
         PartnerEdifactSenderGroups  
      PartnerAckValidation  
      PartnerX12  
      PartnerX12ReceiverGroups  
      PartnerX12SenderGroups  
      PartnerBatchUpdatable  
      PartnerAS2CommonUpdatable  
      PartnerAS2  
```  
  
 Les propriétés globales EDI sont ajoutées au fichier de liaison dans les nœuds suivants.  
  
```  
EDIGlobalProperties  
   EDIGlobalProperties  
      GlobalCommon  
      GlobalEdiFact  
      GlobalX12  
```  
  
 Les nœuds EDI et AS2 sont ajoutés à la fin du fichier de liaison [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le nœud EdiData est ajouté au sous-nœud Tiers sous le nœud Regroupement de tiers, et le nœud EdiGlobalProperties est ajouté après, et au même niveau que, le nœud Regroupement de tiers. Pour plus d’informations sur les nœuds EDI et AS2 dans le fichier de liaison BizTalk, consultez [Structure d’un fichier de liaison](../core/structure-of-a-binding-file.md).  
  
 Le nœud EdiData est facultatif. Toutefois, si le nœud EdiData est présent, les sous-nœuds sous EdiData sont requis. De même, le nœud EdiGlobalProperties est facultatif. Cependant, si le nœud EdiGlobalProperties est présent, les sous-nœuds sous ce dernier sont requis.  
  
 Les nœuds de fichier de liaison EDI et AS2 ne correspondent pas directement aux pages de propriétés dans le Gestionnaire d'accords partenaires dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Certains nœuds de fichier de liaison EDI et AS2 incluent des propriétés utilisées pour les rôles d'expéditeur et des propriétés utilisées pour les rôles de récepteur. Le rôle est indiqué par la propriété IsSender dans le nœud. Pour les nœuds qui ne sont pas utilisés pour les rôles d'expéditeur et de récepteur (PartnerAgreement, PartnerBatchUpdatable, PartnerAS2Updatable et GlobalCommon), IsSender est toujours False.  
  
 Les nœuds PartnerEdifact et PartnerX12 contiennent des propriétés pour les rôles d'expéditeur et de récepteur, qu'IsSender soit défini sur True ou False. Par exemple, PartnerEdifact inclut un champ Una1 (utilisé pour le tiers comme récepteur des échanges), même si IsSender est True. PartnerEdifact inclut également un champ Unb5CheckDup (utilisé pour le tiers comme expéditeur des échanges), même si IsSender est False. Cependant, lorsqu'IsSender est True, ces champs pour le tiers comme récepteur des échanges ne sont pas utilisés dans l'interface utilisateur ou par le moteur, mais ont des valeurs par défaut. De même, lorsqu'IsSender est False, ces champs pour le tiers comme expéditeur des échanges ne sont pas utilisés dans l'interface utilisateur ou par le moteur, mais ont des valeurs par défaut.  
  
 Si la valeur par défaut d'une propriété est null, le champ n'est pas inclus dans le fichier de liaison à moins que ce champ n'ait une valeur.  
  
 Les données du fichier de liaison sont enregistrées dans les tables de la base de données de gestion BizTalk (BizTalkMgmtDb).