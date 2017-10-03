---
title: "Résolution des problèmes de BizTalk ESB Toolkit | Documents Microsoft"
description: "Résoudre les problèmes d’installation et les erreurs courantes avec la boîte à outils ESB dans BizTalk Server"
caps.latest.revision: "2"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1ea2d56-2ace-40f2-80df-8a7489bbfc2e
ms.author: mandia
ms.openlocfilehash: 8fc1305e481de2444a54ea994f8a53da83b2eaed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-biztalk-esb-toolkit"></a>Résoudre les problèmes de BizTalk ESB Toolkit

  
## <a name="installation"></a>Installation  
  
|Problème|Résolution|  
|-----------|----------------|  
|Vous recevez une exception « Erreur d’attribution d’autorisations » lors de l’installation.|Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise les groupes de comptes BizTalk standards, qui doivent exister au cours du processus d’installation ou l’installation échoue. En outre, la boîte à outils suppose une installation autonome où l’ordinateur est membre d’un groupe de travail ou une installation d’entreprise où l’ordinateur est membre d’un domaine.|  
|Importation de l’application échoue avec un message d’erreur qui vous avertit de discordance de niveau de confiance.|Les fichiers de liaison Microsoft.BizTalk.ESB sont configurés pour fonctionner avec la valeur par défaut BizTalkServerApplication et BizTalkServerIsolatedHost, qui à son tour configurées pour s’exécuter en mode non approuvé. Si vous avez modifié votre hôte pour s’exécuter en mode de confiance, le fichier de liaison n’importe pas. Pour corriger ce problème, vous devez modifier le niveau de confiance à non approuvés ou modifier le fichier de liaison pour l’adapter à votre environnement dans le répertoire de \Bindings BizTalk Toolkit.|  
|L’authentification Kerberos n’est pas configurée dans Internet Information Services (IIS).|Pour activer l’authentification Kerberos pour IIS, consultez les articles suivants de la Base de connaissances Microsoft :<br /><br /> -   [Comment configurer IIS pour prendre en charge le protocole Kerberos et le protocole NTLM pour l’authentification réseau](http://go.microsoft.com/fwlink/?LinkId=188566)<br />-   [L’activation de processus IIS utilise l’authentification Kerberos sur un ordinateur qui n’est pas un contrôleur de domaine](http://go.microsoft.com/fwlink/?LinkId=188567)<br />-   [Vous ne pouvez pas configurer les protocoles Negotiate ou NTLM pour l’authentification intégrée Windows dans le Gestionnaire IIS pour les Services Internet (IIS) 7.0](http://go.microsoft.com/fwlink/?LinkId=188568)|  
  
## <a name="general-issues"></a>Problèmes généraux  
  
|Problème|Résolution|  
|-----------|----------------|  
|Vous recevez une exception « Traitement SOAP interne » lors de l’envoi d’un message au service Web de rampe d’entrée d’itinéraire ESB générique.|Utilisez la Console Administration de BizTalk Server pour vous assurer que l’application Microsoft.Practices.ESB est en cours d’exécution ; Si elle n’est pas en cours d’exécution, démarrez-le.|  
|Messages d’exception ne s’affichent pas dans le site portail de gestion ESB.|Vérifiez la page Présentation du groupe administrateur BizTalk et le journal des événements Windows pour les entrées qui indiquent des échecs pour envoyer des messages. Vous devrez peut-être reconfigurer l’exception : adaptateur d’envoi (partie de l’application Microsoft.Practices.ESB) pour correspondre à votre environnement. En outre, sachez que la fonctionnalité de routage des messages a échoué BizTalk et l’infrastructure de gestion BizTalk ESB Toolkit Exception génèrent des messages des exceptions. Par conséquent, vérifiez que vous activez le **itinéraire sur les Messages d’échec** option pour l’envoi et ports de réception.|  
|Lors de l’utilisation d’un service WCF avec un programme de résolution statique, vous recevez une exception d’action SOAP non valide.|Si l’action SOAP du service WCF n’inclut pas l’espace de noms cible, définissez la valeur de l’action SOAP dans le format suivant dans le paramètre du programme de résolution : {action} pour indiquer que l’espace de noms cible ne sera pas concaténée par le moteur de base d’ESB Toolkit lors de l’exécution.|