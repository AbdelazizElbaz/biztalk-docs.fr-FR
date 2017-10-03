---
title: Moteur de Validation de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message validation engine
- errors, validating
- XML validation
- parsing validation
- BRE policies, validating
- errors, messages
- messages, errors
- validating, messages
- validating, BRE policies
- validating, XML
- messages, validating
- validating, errors
- validating, parsing
ms.assetid: 4ba0b75e-665b-4771-b04f-5bc3e90d83f0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbdcb375c04e4c9684b2a805c7a7a7315f46f83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-validation-engine"></a>Moteur de Validation de message
Une des fonctionnalités plus importantes fournies par [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] est la capacité à valider entièrement les messages SWIFT reçus à partir de systèmes back-end destiné au réseau rapide ou reçus à partir du réseau rapide (envoyé par les partenaires commerciaux). Validation des messages SWIFT sortants garantit que les messages sont conformes aux normes SWIFT et que le réseau SWIFT pas rejette les messages.  
  
 Validation des messages SWIFT entrants garantit que les messages reçus à partir d’autres institutions financières obéissent aux règles de contrats particuliers (règles d’entreprise) spécifiques à la relation. Dans les deux cas, la possibilité de valider et d’intercepter les erreurs avant de valider un message permet de réduire les coûts de transaction et le coût total de possession (TCO).  
  
 La liste suivante décrit les quatre parties qui composent le moteur de validation A4SWIFT :  
  
-   Validation structurelle effectuée par l’Analyseur de fichier plat  
  
-   Validation des données effectuée par le lecteur de validation de XML  
  
-   Réseau rapide et l’utilisation de règle de validation effectués par le moteur de règles d’entreprise (BRE)  
  
-   Marquage de message et l’erreur « meilleur effort » de collecte  
  
## <a name="structural-validation-parsing"></a>Validation structurelle (analyse)  
 A4SWIFT analyse les messages de fichier plat SWIFT par rapport aux schémas XSD définies pour chaque type de message SWIFT conformément à la norme SWIFT. L’analyse d’un fichier plat au format XML garantit que le fichier plat est structurellement correct. L’analyse génère également XML qui est plus facile à lire, manipuler ou transformer dans d’autres formats ou les types de messages. Vous pouvez également valider le XML par rapport à la validité des données du schéma et utiliser le moteur de règles d’entreprise (BRE) pour des évaluations plus complexes.  
  
 Le désassembleur SWIFT appelle l’Analyseur de fichier plat BizTalk pour analyser les messages de fichier plat SWIFT appelés par le désassembleur SWIFT. Le désassembleur SWIFT enregistre dans une collection d’erreurs, les détails de toutes les erreurs rencontrées lors de l’analyse et tente toujours de continuer l’analyse des données dans le but pour collecter les erreurs de structurels autant que possible sur le premier test. Toutefois, la plupart des erreurs d’analyse sont irrécupérables et arrêter le traitement des messages à la première erreur.  
  
 Pour plus d’informations sur la validation structurelle, consultez [utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md).  
  
## <a name="data-validation-xml-validation"></a>Validation des données (Validation XML)  
 Vous pouvez définir des messages SWIFT qui passent d’une validation structurelle en tant que XML bien formé conformes aux schémas XSD de défini. A4SWIFT génère le code XML pour les messages SWIFT structurellement valides lors de l’étape d’analyse. A4SWIFT peut alors valider ce document XML pour l’exactitude des données par rapport aux contraintes définies dans le schéma XSD correspondant.  
  
 Ces contraintes incluent notamment typage de données, la longueur et les plages de valeurs définies conformément à la SWIFT standard. Le désassembleur SWIFT appelle le code XML lecteur pour effectuer une validation de données de validation.  
  
 Le désassembleur SWIFT enregistre dans une collection d’erreurs, les détails de toutes les erreurs rencontrées pendant la validation du XML et continue de valider les données restantes pour collecter les erreurs de validation XML autant que possible sur le premier test. (Contrairement à l’analyse, la continuation de la validation XML est garantie.)  
  
 Pour plus d’informations sur la validation des données, consultez [utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md).  
  
## <a name="swift-network-and-usage-rule-validation-bre-validation"></a>Réseau SWIFT et Validation de la règle d’utilisation (Validation BRE)  
 A4SWIFT valide le fichier XML pour les messages SWIFT structurellement valides d’exactitude au niveau de l’entreprise par rapport aux stratégies de moteur de règles d’entreprise (BRE). Ces stratégies incluent l’application des règles de réseau et l’utilisation rapide et des autres règles de champ croisé complexes définies conformément à la norme SWIFT. Le désassembleur SWIFT appelle le moteur BRE pour effectuer la validation au niveau de l’entreprise.  
  
 Le désassembleur SWIFT enregistre dans une collection d’erreurs, les détails de toutes les erreurs rencontrées lors de la validation de BRE et continue de valider les données restantes pour collecter les erreurs de validation BRE autant que possible sur le premier test. (Comme la validation XML, continuation de validation du moteur BRE est garantie.)  
  
 Pour plus d’informations sur la validation de règle SWIFT réseau et l’utilisation, consultez [fonctionne avec les stratégies BRE](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md).  
  
## <a name="validation-failures-and-message-marking"></a>Échecs de validation et le marquage du Message  
 A4SWIFT collecte des erreurs de validation et les détails de chaque étape de validation de message : l’analyse de structure, de la validation XML et de la validation de BRE. A4SWIFT collecte ces erreurs à l’aide d’une heuristique « meilleur effort » pour collecter d’autant plus d’informations sur un message d’erreur que possible. Cette fonctionnalité permet à un message d’échec pour toutes les erreurs interceptées et signalés en une seule fois au lieu d’utiliser plusieurs itérations de soumission, valider, échec, corriger, soumettez à nouveau.  
  
 Les messages qui ont au moins une erreur s’est produite au cours de n’importe quelle étape de validation dans la collection d’erreurs sont considérés comme non valides et ont échoué. A4SWIFT publie ces messages dans la base de données MessageBox, mais ils sont marqués avec des propriétés promues pour indiquer que le message d’échec de la validation et de rapport nombre d’erreurs pour chaque étape de validation.  
  
 Outre les propriétés promues, A4SWIFT sérialise la collection d’erreurs en XML et joint la collection dans le cadre une « erreur » du message à parties multiples. Le message final se compose du message ayant échoué dans le corps et XML de collection d’erreurs dans la partie de l’erreur et a été amélioré avec A4SWIFT promu les propriétés qui indiquent un état d’échec. Le désassembleur SWIFT publie ce message à parties multiples dans la base de données MessageBox.  
  
 Ports d’envoi BizTalk ou orchestrations peuvent récupérer des messages ayant échoué à partir de la base de données MessageBox en vous abonnant à l’A4SWIFT promu des propriétés spéciales. Vous pouvez créer des abonnements pour récupérer tous les messages ayant échoué ou uniquement les messages avec un certain nombre d’erreurs à partir des étapes de validation spécifiques.  
  
 Après la récupération d’un message ayant échoué, vous pouvez l’envoyer à une application de création de rapports, une application de réparation ou de processus ou un référentiel de l’échec, ou vous pouvez l’ignorer.  
  
 Cette possibilité de s’abonner aux messages ayant échoué (et pour distinguer les différents types d’échecs dans l’abonnement), associée à la collection d’erreurs de riche en informations XML associé à chaque message ayant échoué, constitue une infrastructure puissante pour le développement d’erreurs simple rapports applications, tel que fournies par la réparation de message et la nouvelle fonctionnalité d’envoi installé par le programme d’installation A4SWIFT.  
  
 Pour plus d’informations sur les échecs de validation et le marquage du message, consultez [utilisation des abonnements de Message d’échec de](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator pour SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)