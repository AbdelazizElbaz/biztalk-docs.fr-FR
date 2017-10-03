---
title: "Problèmes connus avec la sécurité AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b291e000-630d-49a1-8e19-f76c4dfee294
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb633e092ed568bb3817df7be788364934be446
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-as2-security"></a>Problèmes connus avec la sécurité AS2
Cette rubrique décrit les problèmes connus de sécurité en relation avec les solutions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] AS2.  
  
## <a name="the-as2-decoder-will-not-validate-that-a-certificate-is-configured-on-the-host-or-for-the-destination-party"></a>Le décodeur AS2 ne valide pas le fait qu'un certificat soit configuré sur l'hôte ou pour le tiers de destination  
 Le décodeur AS2 déchiffre un message à condition que le certificat privé relatif à ce dernier soit configuré dans le magasin de certificats. En revanche, le décodeur AS2 ne valide pas le fait que le certificat de déchiffrement soit identique au certificat configuré sur l'hôte. Le message reçu peut être chiffré avec plusieurs certificats.  
  
## <a name="storing-as2-messages-in-wire-format-can-lead-to-a-security-issue"></a>Le stockage des messages AS2 au format câble peut provoquer un problème de sécurité  
 Dans les cas où les certificats ne sont pas utilisés, il n'est pas recommandé de stocker les messages AS2 au format câble dans la base de données de réception de non-répudiation (NRR), sous peine d'affecter la sécurité.  
  
## <a name="messages-or-mdns-to-be-stored-in-the-nrr-database-should-be-signed"></a>Les messages ou MDN à stocker dans la base de données de réception de non-répudiation (NRR) doivent être signés  
 Pour garantir la non-répudiation de réception, vous devez établir l'authentification et l'intégrité des messages. La méthode recommandée pour cela consiste à utiliser une signature numérique sur le message. Par conséquent, si vous configurez les propriétés de tiers AS2 pour stocker des messages ou des MDN dans la base de données de non-répudiation, vous devez configurer les propriétés AS2 de façon à signer les messages ou MDN que vous comptez stocker.  
  
## <a name="biztalk-server-will-be-unable-to-decrypt-a-message-saved-in-wire-format-if-the-certificate-is-not-valid"></a>BizTalk Server ne peut pas déchiffrer un message enregistré au format câble si le certificat n'est pas valide  
 **Symptôme**  
  
 BizTalk Server ne peut pas déchiffrer un message AS2 entrant enregistré au format câble dans la base de données de non-répudiation.  
  
 **Cause possible**  
  
 Le certificat requis pour déchiffrer le message a expiré ou été révoqué. La probabilité que cela se produise est supérieure si une certaine période s'est écoulée depuis l'enregistrement du message AS2 dans la base de données de non-répudiation. Si cela ce produit, il se peut que vous n'ayez pas d'accès immédiat à un certificat valide pour le message.  
  
 **Résolution**  
  
 Acquérir un certificat valide pour le déchiffrement du message.  
  
## <a name="the-inner-envelope-of-a-signed-as2-message-must-not-be-changed-after-the-signature-has-been-calculated"></a>L'enveloppe interne d'un message AS2 signé ne doit pas être modifiée une fois la signature calculée  
 Une fois un message AS2 signé, la signature est calculée sur la base des en-têtes et de la charge de l'enveloppe interne. En cas de modification de l'enveloppe interne après le calcul de la signature, la signature est endommagée. Vous pouvez modifier les en-têtes de limite ou tout ce qui est situé à l'extérieur de ces derniers, mais pas leur contenu.  
  
## <a name="use-the-same-logon-for-the-in-process-host-instance-and-the-isolated-host-instance-to-ensure-that-personal-store-is-recognized"></a>Utilisez le même nom de connexion pour l'instance de l'hôte In-process et l'instance de l'hôte isolé pour vous assurer que le magasin Personnel est reconnu  
 Le magasin de certificats Personnels sera disponible pour le traitement des messages uniquement si le profil utilisateur est chargé pour l'utilisateur dont les informations d'identification sont associées à l'instance hôte. Le magasin Personnel est utilisé pour les certificats de signature et de déchiffrement (la clé propre privée de l'utilisateur). Le profil utilisateur est chargé par défaut pour l'instance hôte In-process ; toutefois, il n'est pas chargé par défaut pour l'instance hôte isolé. Vous pouvez faire en sorte qu'une application charge le profil utilisateur pour l'hôte isolé.  Vous pouvez également contourner ce problème en utilisant le même nom de connexion pour l'instance hôte In-process et l'instance hôte isolé.  
  
 Plutôt que de faire charger le profil utilisateur par une application, vous pouvez créer un service vide pour charger le profil. Pour plus d’informations sur la création d’un service vide, consultez [Comment : créer des Services Windows](http://go.microsoft.com/fwlink/?LinkId=196492). Après avoir créé le service, ouvrez la boîte de dialogue Gestion de l’ordinateur, ouvrez la boîte de dialogue Propriétés pour le service, cliquez sur le **session** onglet, sélectionnez **ce compte**, entrez le nom d’ouverture de session utilisé pour le isolé d’instance d’hôte, puis cliquez sur **OK**. Vous pouvez démarrer manuellement le serveur pour charger le profil utilisateur de cet utilisateur de connexion.  
  
## <a name="the-key-usage-attribute-of-a-certificate-must-match-the-certificates-use"></a>L'attribut Utilisation de la clé d'un certificat doit correspondre à l'utilisation du certificat  
 Les certificats utilisés pour le transport AS2 doivent avoir les attributs requis pour l'utilisation prévue. Pour la signature et la vérification de signature, l'attribut Utilisation de la clé du certificat doit être défini sur Signature numérique. Pour le chiffrement et le déchiffrement, l'attribut Utilisation de la clé du certificat doit être défini sur Chiffrement des données ou Chiffrement de clés. Vous pouvez vérifier l'attribut Utilisation de la clé en double-cliquant sur le certificat, puis en cliquant sur l'onglet Détails de la boîte de dialogue Certificat et en vérifiant le champ Utilisation de la clé.  
  
## <a name="the-certificate-resolution-list-will-be-verified-for-an-outgoing-mdn-if-the-as2-to-property-is-not-set-for-the-party"></a>La liste de résolution des certificats est vérifiée pour un MDN sortant si la propriété AS2-To n'est pas définie pour le tiers  
 Dans l'accord par défaut pour un MDN sortant, la vérification de la liste de résolution des certificats est effectuée. Si vous ne voulez pas que cette vérification ait lieu, vérifiez que la propriété AS2-To correcte est définie, de façon à ce que le tiers qui reçoit puisse être résolu et les propriétés du tiers déterminées. Si c'est le cas, l'accord par défaut qui invite à vérifier la liste de résolution des certificats n'est pas utilisé. Vous devez également désactiver la propriété Vérifier la liste de révocation des certificats de la page Général des propriétés de tiers AS2.