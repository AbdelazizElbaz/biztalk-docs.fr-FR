---
title: "L’accès à la propriété en-tête en cours d’exécution à partir d’un exemple d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2059eb2c-50a3-4618-a6ec-faa1a9e5d368
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ddbb2ea7ef978c0e5eae07835d5a9c1320bbc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-header-property-access-from-an-orchestration-sample"></a>L’accès à la propriété en-tête en cours d’exécution à partir d’un exemple d’Orchestration
Cette partie de l’exemple illustre comment l’architecture ESB promeut les métadonnées d’en-tête JMS dans les propriétés de contexte de message, qui a accès au code et des composants dans les orchestrations dans Microsoft BizTalk. L’exemple inclut un pipeline de réception qui contient une instance du composant ESB JMS qui promeut les métadonnées d’en-tête JMS dans les propriétés de contexte de message.  
  
 Le port de réception transmet le message à une orchestration nommée JMSRouter qui Récupère le nom de la file d’attente affecté par l’utilitaire RfhUtil (et envoyés dans les métadonnées de l’en-tête) à partir des propriétés de contexte du message. L’orchestration affecte ce nom de file d’attente pour un port d’envoi dynamique et envoie le message à ce port.  
  
 Un pipeline d’envoi pour le port contient une instance du composant ESB JMS rétrograde les propriétés de contexte de message dans les métadonnées d’en-tête JMS.  
  
 **Pour exécuter l’exemple d’accès à la propriété en-tête**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
2.  Exécutez l’utilitaire IBM RfhUtil ; Sélectionnez le Gestionnaire de file d’attente nommé ESB. JMS. Sample.QueueManager dans la première liste déroulante pour se connecter à ce gestionnaire de file d’attente, comme dans 1 partie de cet exemple.  
  
3.  Dans la deuxième liste déroulante, sélectionnez la file d’attente cible sortant nommé ESB. JMS. EXEMPLE. SENDTOBIZTALK.  
  
4.  Cliquez sur le **ReadFile** bouton dans l’utilitaire RfhUtil et cliquez sur le fichier de message de test nommé TEST-000128. JMS situé dans le sous-dossier nommé \Source\Samples\JMS\Test\Data\Load\\. Ce fichier contient un lot de messages de test 128, mais l’utilitaire charge seul le premier.  
  
5.  Cliquez sur le **RFH** onglet et assurez-vous que seuls les **JMS** case à cocher est activée.  
  
6.  Cliquez sur le **jms** onglet et assurez-vous que le texte sélectionné **répondre à** file d’attente est ESB. JMS. EXEMPLE. RÉPONSE et que le texte sélectionné **file d’attente de Destination** est ESB. JMS. EXEMPLE. DYNAMICQ2.  
  
7.  Cliquez sur le **principal** onglet, puis cliquez sur le **Q d’écrire** bouton pour écrire le message dans la file d’attente.  
  
8.  Après un certain délai pendant que l’application s’exécute, le message de sortie ESB apparaît dans l’architecture ESB. JMS. EXEMPLE. File d’attente de DYNAMICQ2. Ouvrez l’Explorateur de file d’attente WebSphere et parcourir les files d’attente pour le confirmer.  
  
## <a name="how-the-sample-works"></a>Fonctionne de l’exemple  
 À l’intérieur de l’orchestration, code peut accéder aux valeurs qui étaient dans les en-têtes JMS en chargeant le message dans une **XmlDocument** de l’instance, comme indiqué dans le code suivant.  
  
```csharp  
if (null != InboundMsg(  
    Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData))  
{     
  jmsInfo.LoadXml(InboundMsg(  
     Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData));  
  if (null != jmsInfo)  
  {  
    if (null != jmsInfo.SelectSingleNode("//Dst"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Dst");  
      destinationQueue = xElement.InnerText.ToUpper(  
                         System.Globalization.CultureInfo.CurrentCulture);  
    }  
    if (null != jmsInfo.SelectSingleNode("//Rto"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Rto");  
      replyToQueue = xElement.InnerText.ToUpper(  
                     System.Globalization.CultureInfo.CurrentCulture);  
    }  
  }  
}  
```  
  
 En outre, le code peut accéder à toutes les propriétés de contexte MQMD du message.