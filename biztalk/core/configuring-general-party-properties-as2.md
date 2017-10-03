---
title: "Configuration des propriétés de tiers générales (AS2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9a4dbd0-8849-403a-af82-58ee0b10f85a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deba3ae710b916552095ce66d53813797d8da8da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-party-properties-as2"></a>Configuration des propriétés de tiers générales (AS2)
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
  
3.  Sur le **Ports d’envoi** page de la **propriétés de tiers** boîte de dialogue zone, procédez comme suit :  
  
    > [!NOTE]
    >  Dans [!INCLUDE[prague](../includes/prague-md.md)], l'association de ports d'envoi est effectuée au niveau de l'accord. Le **Ports d’envoi** page est disponible dans le cadre des propriétés du tiers uniquement pour la compatibilité descendante. Chaque fois que vous associez un port d'envoi à un accord, le paramètre de port d'envoi est propagé au paramètre du tiers et l'association de ports d'envoi est visible dans cette page. L'inverse n'est toutefois pas vrai. Vous ne pouvez pas associer un port d'envoi à un tiers, puis rendre ce port d'envoi automatiquement disponible dans le cadre des paramètres de l'accord. Pour plus d'informations sur l'association des ports d'envoi à l'accord, voir ici.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Ports d’envoi - nom**|Dans la liste déroulante, sélectionner un port d'envoi à lier à ce tiers.|  
    |**Ports d’envoi - URI**|Afficher l'adresse du port d'envoi.|  
    |**Supprimer**|Supprimer du tiers le port d'envoi sélectionné.|  
    |**Propriétés**|Cliquez pour afficher les **propriétés de Port d’envoi** boîte de dialogue pour le port d’envoi sélectionné.|  
  
    > [!NOTE]
    >  BizTalk Server peut déterminer le tiers auquel envoyer le message en faisant correspondre le port d'envoi qui s'abonne au message avec le port d'envoi associé à un tiers. Cela peut aussi se faire à l'aide des propriétés de contexte. Pour plus d’informations, consultez [résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
4.  Sur le **certificat** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Parcourir**|Cliquez pour afficher les **sélectionner un certificat** boîte de dialogue, où vous sélectionnez le certificat de signature dans le magasin de certificats ordinateur Local ou d’autres personnes à appliquer aux messages transmis au tiers.|  
    |**Nom commun**|Afficher une description du certificat sélectionné.|  
    |**Empreinte numérique**|Afficher l'empreinte du certificat de clé privée utilisée pour la résolution du tiers et la vérification de signature. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).|  
    |**Supprimer le certificat**|Cliquer pour supprimer le certificat affiché.|  
  
    > [!NOTE]
    >  Le certificat que vous spécifiez pour un tiers est utilisé pour vérifier la signature d'un message AS2 ou MDN envoyé par ce tiers. Le certificat utilisé pour vérifier une signature pour un tiers doit se différencier des certificats utilisés pour vérifier les signatures pour d'autres tiers. Pour plus d’informations sur les certificats utilisés avec les messages AS2, consultez [sécurité AS2](../core/as2-security.md). Vous pouvez être amené à installer et définir des certificats pour la signature sortante, la vérification de la signature entrante, le chiffrement de sortie et le déchiffrement d'entrée.  
  
5.  Cliquez sur **appliquer** pour accepter les propriétés, ou cliquez sur **OK** pour terminer la configuration. Les deux actions valident les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés AS2](../core/configuring-as2-properties.md)