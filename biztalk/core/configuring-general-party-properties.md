---
title: "Configuration des propriétés de tiers générales | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbabf7e5-6388-4900-ad47-cf5d5af396b5
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4bb40e943cc06f298db01142590e2a133c1ee05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-party-properties"></a>Configuration des propriétés de tiers générales
Un tiers ou un partenaire commercial représente une organisation participant à une relation commerciale. Les propriétés du tiers contiennent les informations suivantes :  
  
-   Informations d'ordre général, telles que le nom du tiers  
  
-   Ports d'envoi associés au tiers  
  
-   Certificats associés au tiers  
  
 Pour plus d’informations sur les parties ou les partenaires commerciaux, consultez [partenaires commerciaux](../core/trading-partners-and-business-profiles.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-party-properties"></a>Pour configurer les propriétés de tiers  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Sur le **général** page de la **propriétés de tiers** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrer un nom de tiers.|  
    |**BizTalk local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers**|Cochez cette case pour spécifier que le tiers représente le même partenaire commercial qui héberge également [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. **Important :** pour un module de plateforme sécurisée deux tiers solution qui utilise des pipelines de l’emploi fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez sélectionner cette case à cocher pour au moins un tiers. **Remarque :** si vous désactivez cette case à cocher, certaines propriétés seront désactivées lors de la création d’un accord pour ce tiers.|  
    |**Propriétés supplémentaires – nom / valeur**|Entrez une paire nom-valeur pour mémoriser toute information sur le tiers. Vous pouvez ajouter autant de paires nom-valeur que vous voulez. **Remarque :** les paires nom-valeur ne sont pas utilisés par BizTalk Server pour tout traitement, ces données sont à titre d’information uniquement.|  
    |**Delete**|Cliquez pour supprimer la paire nom-valeur sélectionnée.|  
  
3.  Sur le **Ports d’envoi** page de la **propriétés de tiers** boîte de dialogue zone, procédez comme suit.  
  
    > [!NOTE]
    >  Dans [!INCLUDE[prague](../includes/prague-md.md)], l'association de ports d'envoi est effectuée au niveau de l'accord. Le **Ports d’envoi** page est disponible dans le cadre des propriétés du tiers uniquement pour la compatibilité descendante. Chaque fois que vous associez un port d'envoi à un accord, le paramètre de port d'envoi est propagé au paramètre du tiers et l'association de ports d'envoi est visible dans cette page. L'inverse n'est toutefois pas vrai. Vous ne pouvez pas associer un port d'envoi à un tiers, puis rendre ce port d'envoi automatiquement disponible dans le cadre des paramètres de l'accord. Pour plus d’informations sur l’association de ports d’envoi à l’accord, consultez [configuration envoyer Association de ports (X12)](../core/configuring-send-port-association-x12.md) ou [configuration envoyer Port Association (EDIFACT)](../core/configuring-send-port-association-edifact.md).  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Ports d’envoi - nom**|Dans la liste déroulante, sélectionner un port d'envoi à lier à ce tiers.|  
    |**Ports d’envoi - URI**|Afficher l'adresse du port d'envoi.|  
    |**Supprimer**|Supprimer du tiers le port d'envoi sélectionné.|  
    |**Propriétés**|Cliquez pour afficher les **propriétés de Port d’envoi** boîte de dialogue pour le port d’envoi sélectionné.|  
  
4.  Sur le **certificat** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Parcourir**|Cliquez pour afficher les **sélectionner un certificat** boîte de dialogue, où vous sélectionnez le certificat de signature dans le magasin de certificats ordinateur Local ou d’autres personnes à appliquer aux messages transmis au tiers.|  
    |**Nom commun**|Afficher une description du certificat sélectionné.|  
    |**Empreinte numérique**|Afficher l'empreinte du certificat de clé privée utilisée pour la résolution du tiers et la vérification de signature. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).|  
    |**Supprimer le certificat**|Cliquer pour supprimer le certificat affiché.|  
  
5.  Cliquez sur **appliquer** pour accepter les propriétés, ou cliquez sur **OK** pour terminer la configuration. Les deux actions valident les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)