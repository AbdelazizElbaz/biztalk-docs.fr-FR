---
title: "Dépannage des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, troubleshooting
- troubleshooting, acknowledgements
ms.assetid: faed356e-f5fc-4920-a9f9-82eca0ad7d67
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecbbb22498cfd3d451c0b8c75c8e6f4502c2364d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-acknowledgments"></a>Dépannage des accusés de réception
Traite des problèmes liés à [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] accusés de réception.  
  
## <a name="acknowledgments-are-not-generated"></a>Accusés de réception ne sont pas générés.  
 Il existe plusieurs causes possibles pour les accusés de réception (ACK) n’a été généré ou reçu. Passez en revue la liste suivante des problèmes potentiels.  
  
### <a name="symptom"></a>Symptôme  
 Accusés de réception ne sont pas générés lorsque vous mettez à jour les informations du tiers dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Explorer de Configuration pour générer des accusés de réception.  
  
**Cause possible** : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] met en cache et actualise les informations de configuration de tiers toutes les 15 minutes.  
  
**Résolution** : attendez au moins 15 minutes pour le cache actualiser ou redémarrer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour les modifications prennent effet immédiatement.  
  
### <a name="symptom"></a>Symptôme  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ne génère pas d’accusés de réception et les erreurs d’événement apparaissent dans le journal des événements.  
  
**Cause possible** : un accusé de réception ne peut pas être généré lorsqu’un lot dans / lots message contient un champ FHS11 vide.  
  
**Résolution** : Assurez-vous que vos messages ont un champ FHS11 correctement mis en forme et rempli.  
  
### <a name="symptom"></a>Symptôme  
 Votre application ne peut pas générer ou recevoir un accusé de réception.  
  
**Cause possible** : empêchent des informations incorrectes dans le champ MSH3 de votre message [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] d’envoyer le message aux accusés de réception.  
  
**Résolution** : Assurez-vous que vos messages ont un champ MSH3 correctement mis en forme et rempli.  
  
## <a name="acknowledgments-are-suspended-or-not-routed-to-the-send-party"></a>Accusés de réception sont suspendus ou pas routés vers le tiers d’envoi  
  
### <a name="symptom"></a>Symptôme  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]envoie des messages à une carte bidirectionnelle sans génération d’accusés de réception.  
  
**Cause possible** : l’abonnement de message n’est pas configuré correctement.  
  
**Résolution** : Assurez-vous que les abonnements aux messages soient présent et configuré correctement.  
  
## <a name="suspended-acknowledgments"></a>Accusés de réception suspendus  
  
### <a name="symptom"></a>Symptôme  
 Accusés de réception sont suspendus avec le message d’erreur « Délimiteur figurant dans le champ » lorsque vous avez configuré le tiers pour que l’encodage de caractères contenant les caractères de délimitation telles que @-! $.  
  
**Cause possible** : le message contient des caractères tels que le point (.) ou un trait d’union (-). Lors de la génération les accusés de réception, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] inclut «. » et «- » pour la valeur d’horodateur.  
  
**Résolution** : désactiver la validation dans le pipeline d’envoi afin d’éviter ces erreurs.  
  
## <a name="biztalk-server-generates-an-error-about-missing-ack-when-using-2-way-mllp-adapter"></a>BizTalk Server génère une erreur manquants de l’accusé de réception lors de l’utilisation de l’adaptateur MLLP à 2 facteurs  
  
### <a name="symptom"></a>Symptôme  
 Vous obtenez l’erreur suivante ou similaire dans le journal des événements :  
  
 « Impossible de recevoir l’accusé de réception à partir du réseau en raison d’une erreur « Exception de HRESULT : 0xC0C01662 « »  
  
**Cause possible** : à l’aide de 1-méthode de réception et le port d’envoi bidirectionnel 2, c’est le cas BizTalk n’a pas d’un port de réception correspondant pour renvoyer le message reçu à partir du port d’envoi bidirectionnel 2.  
  
**Résolution** : il s’agit par conception, et vous pouvez ignorer le message d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
[Problèmes connus et dépannage dans HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)