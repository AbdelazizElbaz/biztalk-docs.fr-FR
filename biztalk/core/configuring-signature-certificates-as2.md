---
title: Configuration des certificats de Signature (AS2) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8539e210-1656-4fff-b026-36b81689061f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32a52962976c2db62de902906f53f5c270e2c7c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-signature-certificates-as2"></a>Configuration des certificats de signature (AS2)
Dans le cadre des paramètres de cette page, vous pouvez spécifier les certificats à utiliser pour signer les messages sortants et le MDN qui résout cet accord. Les paramètres de cette page remplacent les paramètres de certificat fournis dans le cadre des propriétés du groupe BizTalk. Pour plus d’informations sur l’utilisation des certificats, consultez [configuration des certificats pour AS2](../core/configuring-certificates-for-as2.md).  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-agreement-level-signature-certificate"></a>Pour configurer le certificat de signature au niveau de l'accord  
  
1.  Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md). Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, cliquez sur **certificats de Signature**.  
  
3.  Sélectionnez le **groupe de remplacement de certificat de signature** case à cocher pour utiliser le certificat fourni dans cette page pour la signature des messages AS2 sortants et MDN.  
  
4.  Cliquez sur **Parcourir** pour afficher les **sélectionner un certificat** boîte de dialogue, dans laquelle vous sélectionnez le certificat de signature à appliquer aux messages transmis par ce tiers.  
  
5.  Le **nom commun** zone de texte affiche une description du certificat sélectionné.  
  
6.  Le **l’empreinte numérique** zone de texte affiche l’empreinte numérique du certificat. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).  
  
7.  Cliquez sur **supprimer le certificat** pour supprimer le certificat sélectionné.  
  
8.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés d’accord AS2](../core/configuring-as2-agreement-properties.md)