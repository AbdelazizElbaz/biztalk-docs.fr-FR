---
title: Meilleures pratiques pour la gestion Certificates1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, certificates
- certificates, security
- security, certificates
- certificates, best practices
- best practices, security
- security, best practices
ms.assetid: cd182df4-0fcd-409c-9221-89f92e069f07
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e72d87530e5d080bd98ed55c2d29ca9554430375
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-managing-certificates"></a><span data-ttu-id="5ea0c-102">Méthodes conseillées pour la gestion des certificats</span><span class="sxs-lookup"><span data-stu-id="5ea0c-102">Best Practices for Managing Certificates</span></span>
<span data-ttu-id="5ea0c-103">Cette section présente les meilleures pratiques relatives à la gestion des certificats dans votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ea0c-103">This section provides best practices for managing certificates in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="5ea0c-104">**Effectuer une analyse du modèle de votre environnement**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-104">**Do a Threat Model Analysis of your environment**</span></span>  
  
     <span data-ttu-id="5ea0c-105">Réalisez une analyse du modèle des menaces de votre environnement pour déterminer si les certificats de signature ou de chiffrement permettent de réduire les menaces potentielles.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-105">Do a Threat Model Analysis (TMA) of your environment to determine whether signing or encryption certificates will help you mitigate security threats.</span></span>  
  
-   <span data-ttu-id="5ea0c-106">**Créez un plan pour les certificats de clé publique avec les partenaires**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-106">**Create a plan for public key certificates with partners**</span></span>  
  
     <span data-ttu-id="5ea0c-107">Créez une stratégie pour l'envoi et la réception des certificats de clé publique avec les partenaires.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-107">Create a plan for sending and receiving public key certificates with partners.</span></span> <span data-ttu-id="5ea0c-108">Si vous n'utilisez pas de certificats de signature pour la résolution du tiers, le certificat public peut être joint au message et il n'est pas nécessaire que votre système en inclue une copie.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-108">If you are not using signing certificates for party resolution, the public certificate can be attached to the message, in which case you do not need a copy of the certificate in your system beforehand.</span></span>  
  
-   <span data-ttu-id="5ea0c-109">**Télécharger la liste de révocation de certificats à des intervalles définis**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-109">**Download the certificate revocation list at set intervals**</span></span>  
  
     <span data-ttu-id="5ea0c-110">Téléchargez la liste de révocation des certificats de votre autorité de certification à intervalles définis.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-110">Download the certificate revocation list (CRL) from your certification authority (CA) at set intervals.</span></span> <span data-ttu-id="5ea0c-111">Il est recommandé d'effectuer cette opération une fois par semaine.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-111">We recommend doing this once a week.</span></span> <span data-ttu-id="5ea0c-112">Les listes de révocation des certificats sont téléchargées automatiquement si une autorité de certification existe pour le domaine auquel les serveurs BizTalk sont joints.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-112">The CRLs are downloaded automatically if there is a CA for the domain in which the BizTalk servers are joined.</span></span>  
  
-   <span data-ttu-id="5ea0c-113">**Établissez des instructions avec des partenaires pour l’envoi de clés publiques**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-113">**Establish guidelines with partners for submitting public keys**</span></span>  
  
     <span data-ttu-id="5ea0c-114">Dans le contrat de niveau de service (SLA) passé avec vos partenaires, établissez des instructions pour l'envoi des clés publiques, afin qu'ils vous avertissent lorsque leurs certificats expirent ou sont révoqués.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-114">As part of your Service Level Agreement (SLA) with your partner, establish guidelines for submitting public keys, notifying you when their certificates are about to expire, and notifying you when they revoke a certificate.</span></span>  
  
-   <span data-ttu-id="5ea0c-115">**Vérifier les certificats de signature**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-115">**Verify signing certificates**</span></span>  
  
     <span data-ttu-id="5ea0c-116">Assurez-vous de contrôler la présence de certificats de signature dans la liste de révocation de certificats.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-116">Make sure you verify the signing certificates against the certificate revocation list.</span></span> <span data-ttu-id="5ea0c-117">Pour plus d’informations sur la façon de vérifier la signature des certificats, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="5ea0c-117">For more information about how to verify the signing certificates, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
-   <span data-ttu-id="5ea0c-118">**Éviter les attaques de déni de service pour les signatures numériques**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-118">**Avoid denial of service attacks for digital signatures**</span></span>  
  
     <span data-ttu-id="5ea0c-119">Déterminez ce que vous voulez faire des messages lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas valider la signature numérique.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-119">Determine what you want to do with messages when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot validate the digital signature.</span></span> <span data-ttu-id="5ea0c-120">Définition de la **authentification** propriété sur le port de réception permettra d’éviter les attaques de déni de service.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-120">Setting the **Authentication** property on the receive port will help prevent denial of service attacks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ea0c-121">Le **authentification - supprimer les messages** et **authentification - conserver les messages** des indicateurs sur le port de réception nécessitent que le composant de pipeline Résolution du tiers est configuré correctement, et que les parties sont défini dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-121">The **Authentication - Drop messages** and **Authentication - Keep messages** flags on the receive port require that the Party Resolution pipeline component be configured correctly, and that the parties are defined in BizTalk Server.</span></span> <span data-ttu-id="5ea0c-122">Pour plus d’informations sur la configuration du composant de pipeline Résolution du tiers, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="5ea0c-122">For more information about configuring the Party Resolution pipeline component, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>  
  
-   <span data-ttu-id="5ea0c-123">**Créez des emplacements de réception pour les messages chiffrés et**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-123">**Create separate receive locations for encrypted and unencrypted messages**</span></span>  
  
     <span data-ttu-id="5ea0c-124">Si vous envisagez de recevoir des messages MIME chiffrés de la part de certains partenaires et des messages non chiffrés de la part d'autres partenaires, créez des emplacements de réception distincts dans les différents hôtes pour les messages chiffrés et non chiffrés.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-124">If you plan to receive MIME-encrypted messages from some partners and unencrypted messages from other partners, create separate receive locations in different hosts for encrypted and unencrypted messages.</span></span> <span data-ttu-id="5ea0c-125">Lorsque vous n'attendez que les messages MIME chiffrés, configurez le **autoriser les messages non-MIME** option dans le composant de pipeline MIME/SMIME décoder à **non**.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-125">When you expect only MIME-encrypted messages, configure the **Allow Non MIME Message** option in the Decode MIME/SMIME pipeline component to **No**.</span></span>  
  
-   <span data-ttu-id="5ea0c-126">**Gérer les certificats avec des partenaires**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-126">**Manage certificates with partners**</span></span>  
  
     <span data-ttu-id="5ea0c-127">Utilisez la gestion des certificats dans le cadre de vos méthodes de gestion des partenaires.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-127">Make certificate management part of your partner management practices.</span></span> <span data-ttu-id="5ea0c-128">Lorsque vous ajoutez ou supprimez un tiers de l'environnement BizTalk Server, il est recommandé d'ajouter ou de supprimer le certificat associé à ce tiers.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-128">When you add or remove a party from the BizTalk Server environment, we recommend that you add or remove the certificates associated with that partner.</span></span>  
  
-   <span data-ttu-id="5ea0c-129">**Supprimer les certificats avant de supprimer une instance d’hôte**</span><span class="sxs-lookup"><span data-stu-id="5ea0c-129">**Remove certificates before removing a host instance**</span></span>  
  
     <span data-ttu-id="5ea0c-130">Avant de supprimer une instance d'hôte de BizTalk Server, supprimez les certificats dans le magasin personnel du compte sous lequel l'instance de l'hôte est exécutée.</span><span class="sxs-lookup"><span data-stu-id="5ea0c-130">Before removing a host instance from a BizTalk server, remove the certificates in the personal store of the account under which the host instance is running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea0c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ea0c-131">See Also</span></span>  
 <span data-ttu-id="5ea0c-132">[Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md) </span><span class="sxs-lookup"><span data-stu-id="5ea0c-132">[Managing BizTalk Server Security](../core/managing-biztalk-server-security.md) </span></span>  
 [<span data-ttu-id="5ea0c-133">Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows</span><span class="sxs-lookup"><span data-stu-id="5ea0c-133">Best Practices for Managing Windows Groups and User Accounts</span></span>](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)