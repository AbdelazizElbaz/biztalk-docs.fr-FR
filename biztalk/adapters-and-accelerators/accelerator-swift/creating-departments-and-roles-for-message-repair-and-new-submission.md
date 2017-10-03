---
title: "Création de services et les rôles pour Message Repair et New Submission | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- departments, creating
- creating, roles
- roles, requirements
- roles, creating
- creating, departments
- certificates, messages
- messages, certificates
ms.assetid: 6337bd57-63c5-4d97-b558-ac27d5eb60d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d033ab3910657373f6e48b1f6e6bed076f730b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-departments-and-roles-for-message-repair-and-new-submission"></a>Création de services et les rôles pour Message Repair et New Submission
Message Repair et New Submission implique quatre différentes opérations :  
  
-   Réparation d’un message d’échec de la validation  
  
-   Vérification de la réparation (y compris la régénération de clé)  
  
-   Approbation de la réparation  
  
-   Création d’un nouveau message  
  
 Pour effectuer une de ces opérations, un utilisateur doit assumer le rôle associé à l’opération. Le rôle doit être également une partie du service de traitement (décrite ci-dessous). Pour envoyer le message après avoir effectué une étape dans le flux de travail, l’utilisateur doit signer le message avec un certificat valide avec l’utilisateur.  
  
## <a name="creating-departments-and-roles"></a>Création de rôles et de services  
 Consultez la documentation du client Web de profil.  
  
## <a name="rules-of-role-use"></a>Règles d’utilisation de rôle  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]les utilisateurs, les rôles et les services doivent respecter les règles suivantes :  
  
-   Le flux de travail complet pour un message réparé consiste à réparer et vérifier le message puis l’approuver. Le flux de travail complet pour un message créé consiste à créer, réparer, vérifier, puis l’approuver le message. Les étapes de vérification et approbation sont facultatifs.  
  
-   Flux de travail d’un service doit commencer par un rôle de la création ou la réparation. Si un flux de travail inclut les étapes de création et la réparation (un flux de travail pour un message créé), l’étape de création doit être placée immédiatement avant l’étape de réparation.  
  
-   Un flux de travail pour un message créé doit contenir qu’un seul rôle qui dispose d’une fonctionnalité de création.  
  
-   Chaque flux de travail doit contenir qu’un seul rôle qui dispose d’une fonctionnalité de réparation.  
  
-   Un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur peut être associé à plusieurs rôles, mais aucun utilisateur unique ne peut exécuter plusieurs étapes dans un seul flux de travail. Par exemple, si l’utilisateur A répare un message et l’utilisateur B vérifie le message, puis l’utilisateur A ni l’utilisateur B peut approuver le message.  
  
-   Il n’existe aucune vérification de l’ordre des rôles avec la fonctionnalité de RekeyVerify ou approuver par rapport à d’autres rôles avec la fonctionnalité de RekeyVerify ou approuver.  
  
-   Si un message indiquant que vous avez déjà réparé échoue à nouveau la validation, il revient dans la boîte de réception de réparation dans la bibliothèque de documents du site MRSR. Dans ce cas, les restrictions précédentes sur les rôles de vérification et approbateur (selon qui a déjà effectué un rôle dans le flux de travail) ne s’appliquent plus. Par exemple, si l’utilisateur A des réparations un message, l’utilisateur B rejette le message dans la vérification et réparation de l’utilisateur A le message une deuxième fois, puis un utilisateur autre que l’utilisateur B peut vérifier le message. Si tel est le cas, l’utilisateur B peut approuver le message. Un autre exemple est que si l’utilisateur A crée un message, l’utilisateur B rejette le message de vérification et utilisateur C répare le message, l’utilisateur A pu vérifier le message.  
  
-   Un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur qui crée un message peut également réparer ce message en cas d’échec de validation.  
  
-   Uniquement [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] les utilisateurs du département associé à un flux de travail peuvent effectuer une étape dans le flux de travail. Lorsqu’un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur envoie un message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] vérifie que l’utilisateur a un rôle dans le service associé au message (via l’utilisateur profils (au cas où le service n’est pas par défaut) dans le client web de profil).  
  
-   Un administrateur peut donner à un seul [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur plusieurs rôles au sein d’un service. Un seul utilisateur peut effectuer la réparation, la vérification, une approbation, ou la création ou n’importe quel sous-ensemble de ces rôles, sous réserve des limitations sur n’importe quel un flux de travail décrit ci-dessus.  
  
## <a name="certificates"></a>Certificats  
 Pour envoyer un message sur votre ordinateur local après la réparation, la vérification, l’approbation ou la création, la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur doit signer le message avec son certificat. Pour plus d’informations sur la création de certificats, consultez [l’installation de certificats](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md).  
  
 Pour être en mesure de le réparer, vérifier, approuver ou créer un message en accédant au site MRSR à partir d’un ordinateur client distant, l’utilisateur doit ajouter son certificat dans les certificats - magasin de l’utilisateur actuel/personnel/certificats de leur ordinateur client (l’utilisateur n’a pas être un administrateur pour le faire). En outre, un administrateur sur le serveur doit ajouter le certificat de l’utilisateur (et ceux de tous les autres utilisateurs qui accèdent au serveur à partir de leur ordinateur client) pour les certificats (ordinateur Local) / stocker d’autres personnes/certificats sur le serveur.  
  
 Un seul utilisateur peut avoir plusieurs rôles alloués et doit utiliser le même certificat lorsque vous effectuez une de ces rôles.