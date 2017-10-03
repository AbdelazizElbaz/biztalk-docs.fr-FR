---
title: "Personnalisation des énumérations dans le schéma d’enveloppe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b053d82-753f-4a05-9922-fa5dbd073ba9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b33458d3a7fbc71ea5e2df7603390f10b928113
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-enumerations-in-the-envelope-schema"></a>Personnalisation des énumérations dans le schéma d'enveloppe
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de personnaliser les énumérations de champs d'ID dans le schéma (d'enveloppe) de service. Cela vous permet de recevoir et d'envoyer des échanges contenant des valeurs non standard (étrangères à l'ensemble de valeurs définies par le corps de normes X12) dans les champs d'ID d'expéditeur ou de récepteur de l'enveloppe. Cela permet également de modifier les qualificateurs disponibles dans les listes déroulantes pour les valeurs d'en-tête dans les définitions de propriété d'accord.  
  
> [!IMPORTANT]
>  Lorsque vous modifiez un schéma, cette modification s'applique à toutes les transactions pour la norme en question. Vous ne pouvez pas introduire de modification dans le schéma d'enveloppe pour un seul tiers.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tire la liste des valeurs autorisées des schémas de service statique du fichier Microsoft.BizTalk.Edi.BaseArtifacts.dll fourni avec le produit. Pour étendre l’ensemble de valeurs de base, vous devez développer et déployer une extension de schéma de service. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Fournit des modèles de schéma que vous pouvez utiliser pour modifier les énumérations de service (enveloppe). Ces schémas de service sont X12_ServiceSchemaExtension.xsd et EDIFACT_ServiceSchemaExtension.xsd. Chaque schéma personnalisé aura un des espaces de noms suivants, en fonction de la norme. Il n'est pas possible de modifier cet espace de noms.  
  
|Standard|Espace de noms|  
|--------------|---------------|  
|X 12 et HIPAA|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006`|  
|EDIFACT|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`|  
  
 Vous apportez les modifications au schéma dans l'Éditeur BizTalk de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] (consultez la procédure ci-dessous). Après avoir apporté les modifications requises, vous devez déployer le schéma.  
  
 Tant du côté envoi que du côté réception, quand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide les segments d'enveloppe (ISA et GS pour X12, ou UNB et UNG pour EDIFACT), il vérifie l'existence du schéma de service personnalisé sur la base de son espace de noms. Si le schéma personnalisé est déployé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le fusionne avec le schéma de service ordinaire et utilise des valeurs d'énumération tant personnalisées que standard lorsque c'est spécifié. Vous pouvez personnaliser le schéma pour étendre une liste d'énumération, mais vous ne pouvez pas en retirer de valeurs. Si un schéma personnalisé n'est pas déployé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le schéma de service standard.  
  
 Après le déploiement d'un schéma personnalisé, l'interface utilisateur [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] de la console Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les valeurs d'une énumération personnalisée pour alimenter les listes déroulantes appropriées dans les pages de propriétés [!INCLUDE[TPM_abbrev](../includes/tpm-abbrev-md.md)]. Si vous n'avez pas déployé de schéma personnalité, [!INCLUDE[TPM_abbrev](../includes/tpm-abbrev-md.md)] utilise les valeurs des énumérations dans le schéma de service standard. En outre, le moteur d'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise l'énumération personnalisée pour valider un message.  
  
 Si vous utilisez les outils XML fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour valider une instance avec son enveloppe alors que vous avez personnalisé le schéma de service, vous devez inclure le schéma de service personnalisé dans le projet BizTalk, en plus du ou des schémas de document (informatisé) et, si nécessaire, du schéma de lot. Cela n'est pas nécessaire si vous validez une instance de document informatisé dépourvue d'enveloppe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##  <a name="BKMK_Env_Can"></a>Champs d’enveloppe qui peuvent être modifiées.  
 Seuls les champs d'enveloppe suivants peuvent être modifiés. Seuls ces champs sont inclus dans les schémas d'extension. D'autres champs ajoutés dans le schéma d'extension de service n'auront aucun effet sur le traitement.  
  
|Standard|Champ|  
|--------------|-----------|  
|X 12 et HIPAA|ISA01 – Qualificateur d'autorisation<br /><br /> ISA03 – Qualificateur de sécurité<br /><br /> ISA05 – Qualificateur d'ID d'expéditeur<br /><br /> ISA07 - Qualificateur d'ID de récepteur<br /><br /> GS01 - code fonctionnel<br /><br /> GS07 - Entité responsable|  
|EDIFACT|UNB2.2 - Qualificateur de code de l'expéditeur<br /><br /> UNB3.2 - Qualificateur de code du récepteur|  
  
## <a name="envelope-fields-that-should-not-be-modified"></a>Champs d'enveloppe à ne pas modifier  
 Certains champs de l'enveloppe déterminent des comportements dans le moteur. Par conséquent, vous ne devez pas ajouter de valeurs à une liste d'énumération existante pour aucun de ces champs. Ces champs sont les suivants :  
  
|Standard|Champ|  
|--------------|-----------|  
|X 12 et HIPAA|ISA11 – Identificateur de normes de contrôle d'échange<br /><br /> ISA12 – Numéro de version de contrôle d'échange<br /><br /> ISA14 – Accusé de réception demandé|  
|EDIFACT|UNB1.1 – Identificateur de syntaxe<br /><br /> UNB1.2 – Numéro de version de syntaxe<br /><br /> UNB9 – Demande d'accusé de réception|  
  
### <a name="to-customize-an-enumeration-in-the-envelope-schema"></a>Pour personnaliser une énumération dans le schéma d'enveloppe  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un projet.  
  
2.  Ajoutez le schéma X12_ServiceSchemaExtension.xsd (pour modifier les énumérations X12 ou HIPAA) ou le schéma EDIFACT_ServiceSchemaExtension.xsd figurant dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI à un projet BizTalk dans l'Éditeur BizTalk. Ouvrez le schéma.  
  
3.  Pour modifier les valeurs d’une énumération, sélectionnez celle-ci dans le **propriétés** volet, puis cliquez sur les points de suspension pour ouvrir la **Éditeur d’énumération**. Ajouter à la liste de valeurs, en veillant à ce qu’il existe une valeur sur chaque ligne dans le **valeurs** volet. Cliquez sur **OK**.  
  
    > [!IMPORTANT]
    >  Vous ne pouvez pas modifier l'espace de noms pour le schéma de service. Le schéma doit avoir les mêmes espace de nom et nom de nœud racine que le schéma d'extension original installé avec le produit.  
  
    > [!NOTE]
    >  Si vous ajoutiez un champ aux schémas, il serait ignoré. Seuls les champs répertoriés dans le [enveloppe champs que peut être modifiée](../core/customizing-enumerations-in-the-envelope-schema.md#BKMK_Env_Can) ci-dessus peut être modifié.  
  
4.  Enregistrez le schéma.  
  
5.  Cliquez sur le schéma, puis cliquez sur **déployer**.  
  
    > [!NOTE]
    >  Le schéma doit être déployé dans le groupe BizTalk actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement des schémas EDI](../core/developing-edi-schemas.md)   
 [Modification des schémas EDI](../core/modifying-edi-schemas.md)