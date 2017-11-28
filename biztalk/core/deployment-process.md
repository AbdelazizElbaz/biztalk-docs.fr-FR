---
title: "Processus de déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, deploying
- deploying, SSO
- LogonExternalUser test [SSO]
- security, SSO
- SSO, LogonExternalUser test
- SSO, security
ms.assetid: 7dd4c022-c70b-467a-bf94-dc4ac6029f81
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21be32ec58c90c1fb95134a002bee82ef5d78fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-process"></a><span data-ttu-id="727ba-102">Processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="727ba-102">Deployment Process</span></span>
<span data-ttu-id="727ba-103">La procédure suivante donne une vue d'ensemble du déploiement sécurisé de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="727ba-103">The following steps give a high-level overview of secure deployment of Enterprise Single Sign-On.</span></span> <span data-ttu-id="727ba-104">Pour obtenir des procédures détaillées relatives aux actions à effectuer dans SQL Server, consultez la documentation SQL Server.</span><span class="sxs-lookup"><span data-stu-id="727ba-104">For detailed procedures on the actions to take in SQL Server, see your SQL Server documentation.</span></span>  
  
1.  <span data-ttu-id="727ba-105">Dans le contrôleur de domaine SQL Serveur, utilisez l'Assistant Nouvelle approbation pour créer une approbation dotée des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="727ba-105">On the SQL Server domain controller, use the New Trust Wizard to create a trust with the following properties:</span></span>  
  
    -   <span data-ttu-id="727ba-106">**Nom :** ORCH.com</span><span class="sxs-lookup"><span data-stu-id="727ba-106">**Name:** ORCH.com</span></span>  
  
    -   <span data-ttu-id="727ba-107">**Direction :** bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="727ba-107">**Direction:** Two-way</span></span>  
  
    -   <span data-ttu-id="727ba-108">**Côtés :** ce domaine uniquement</span><span class="sxs-lookup"><span data-stu-id="727ba-108">**Sides:** This domain only</span></span>  
  
    -   <span data-ttu-id="727ba-109">**Sortant de niveau de l’authentification de confiance - domaine Local :** l’authentification sélective</span><span class="sxs-lookup"><span data-stu-id="727ba-109">**Outgoing Trust Authentication Level - Local Domain:** Selective authentication</span></span>  
  
    -   <span data-ttu-id="727ba-110">**Mot de passe :** choisir un mot de passe</span><span class="sxs-lookup"><span data-stu-id="727ba-110">**Password:** Choose a password</span></span>  
  
    -   <span data-ttu-id="727ba-111">**Confirmer l’approbation sortante :** Oui</span><span class="sxs-lookup"><span data-stu-id="727ba-111">**Confirm Outgoing Trust:** Yes</span></span>  
  
    -   <span data-ttu-id="727ba-112">**Confirmer l’approbation entrante :** N°</span><span class="sxs-lookup"><span data-stu-id="727ba-112">**Confirm Incoming Trust:** No</span></span>  
  
2.  <span data-ttu-id="727ba-113">Dans le contrôleur de domaine ORCH.com, utilisez l'Assistant Nouvelle approbation pour créer une approbation dotée des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="727ba-113">On the ORCH.com domain controller, use the New Trust Wizard to create a trust with the following properties:</span></span>  
  
    -   <span data-ttu-id="727ba-114">**Nom :** SQL.com</span><span class="sxs-lookup"><span data-stu-id="727ba-114">**Name:** SQL.com</span></span>  
  
    -   <span data-ttu-id="727ba-115">**Direction :** bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="727ba-115">**Direction:** Two-way</span></span>  
  
    -   <span data-ttu-id="727ba-116">**Côtés :** ce domaine uniquement</span><span class="sxs-lookup"><span data-stu-id="727ba-116">**Sides:** This domain only</span></span>  
  
    -   <span data-ttu-id="727ba-117">**Sortant de niveau de l’authentification de confiance - domaine Local :** l’authentification sélective</span><span class="sxs-lookup"><span data-stu-id="727ba-117">**Outgoing Trust Authentication Level - Local Domain:** Selective authentication</span></span>  
  
    -   <span data-ttu-id="727ba-118">**Mot de passe :** doit être le même que le mot de passe pour ORCH.com</span><span class="sxs-lookup"><span data-stu-id="727ba-118">**Password:** Must be the same as password for ORCH.com</span></span>  
  
    -   <span data-ttu-id="727ba-119">**Confirmer l’approbation sortante :** Oui</span><span class="sxs-lookup"><span data-stu-id="727ba-119">**Confirm Outgoing Trust:** Yes</span></span>  
  
    -   <span data-ttu-id="727ba-120">**Confirmer l’approbation entrante :** N°</span><span class="sxs-lookup"><span data-stu-id="727ba-120">**Confirm Incoming Trust:** No</span></span>  
  
3.  <span data-ttu-id="727ba-121">Dans le contrôleur de domaine ORCH.com, définissez l'approbation du domaine pour les entrées provenant de SQL.COM.</span><span class="sxs-lookup"><span data-stu-id="727ba-121">On the ORCH.com domain controller, set the domain wide trust for Incoming from SQL.COM.</span></span>  
  
4.  <span data-ttu-id="727ba-122">Dans le contrôleur de domaine SQL.com, définissez l'approbation du domaine pour les sorties provenant de ORCH.COM.</span><span class="sxs-lookup"><span data-stu-id="727ba-122">On the SQL.com domain controller, set the domain wide trust for Outgoing from ORCH.COM.</span></span>  
  
5.  <span data-ttu-id="727ba-123">Dans le contrôleur de domaine ORCH.com, élevez le niveau fonctionnel du domaine à Windows Server 2008 SP2 ou Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="727ba-123">On the ORCH.com domain controller, raise the domain functional level to Windows Server 2008 SP2 or Windows Server 2008 R2.</span></span>  
  
6.  <span data-ttu-id="727ba-124">Dans le domaine ORCH, créez les utilisateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="727ba-124">In the ORCH domain, create the following new users:</span></span>  
  
    -   <span data-ttu-id="727ba-125">ORCH\SSOSvcUser</span><span class="sxs-lookup"><span data-stu-id="727ba-125">ORCH\SSOSvcUser</span></span>  
  
    -   <span data-ttu-id="727ba-126">ORCH\TestAppUser</span><span class="sxs-lookup"><span data-stu-id="727ba-126">ORCH\TestAppUser</span></span>  
  
    -   <span data-ttu-id="727ba-127">ORCH\AffAppUser</span><span class="sxs-lookup"><span data-stu-id="727ba-127">ORCH\AffAppUser</span></span>  
  
7.  <span data-ttu-id="727ba-128">Ajouter **agir en tant que partie du système d’exploitation** à SSOSvcUser et TestAppUser.</span><span class="sxs-lookup"><span data-stu-id="727ba-128">Add **Act as part of the operating system** to SSOSvcUser and TestAppUser.</span></span>  
  
8.  <span data-ttu-id="727ba-129">Ajouter **autorisé à authentifier** privilège à ORCH\TestAdmin.</span><span class="sxs-lookup"><span data-stu-id="727ba-129">Add **Allowed to Authenticate** privilege to ORCH\TestAdmin.</span></span>  
  
9. <span data-ttu-id="727ba-130">Ajoutez ORCH\SSOSvcUser à SQL2 dans le domaine SQL.</span><span class="sxs-lookup"><span data-stu-id="727ba-130">Add ORCH\SSOSvcUser to SQL2 in the SQL domain.</span></span> <span data-ttu-id="727ba-131">(Cette étape nécessite l'utilisation de la vue avancée dans Active Directory MMC.)</span><span class="sxs-lookup"><span data-stu-id="727ba-131">(This step requires using Advanced View in Active Directory MMC.)</span></span>  
  
10. <span data-ttu-id="727ba-132">Créez les deux comptes de connexion suivants sur l'ordinateur SQL2 :</span><span class="sxs-lookup"><span data-stu-id="727ba-132">On the SQL2 computer, create the following two new logins:</span></span>  
  
    -   <span data-ttu-id="727ba-133">ORCH\TestAdmin</span><span class="sxs-lookup"><span data-stu-id="727ba-133">ORCH\TestAdmin</span></span>  
  
    -   <span data-ttu-id="727ba-134">ORCH\SSOSvcUser</span><span class="sxs-lookup"><span data-stu-id="727ba-134">ORCH\SSOSvcUser</span></span>  
  
11. <span data-ttu-id="727ba-135">Créez les deux groupes globaux de domaine sur le domaine SQL2 :</span><span class="sxs-lookup"><span data-stu-id="727ba-135">On the SQL2 domain, create two domain global groups:</span></span>  
  
    -   <span data-ttu-id="727ba-136">ORCH\SSOAdminGroup</span><span class="sxs-lookup"><span data-stu-id="727ba-136">ORCH\SSOAdminGroup</span></span>  
  
    -   <span data-ttu-id="727ba-137">ORCH\SSOAffAdminGroup</span><span class="sxs-lookup"><span data-stu-id="727ba-137">ORCH\SSOAffAdminGroup</span></span>  
  
12. <span data-ttu-id="727ba-138">Ajouter **autorisé à authentifier** privilège au groupe ORCH\SSOAdminGroup.</span><span class="sxs-lookup"><span data-stu-id="727ba-138">Add **Allowed to Authenticate** privilege to the ORCH\SSOAdminGroup group.</span></span>  
  
13. <span data-ttu-id="727ba-139">Créez le compte de connexion suivant sur la base de données SQL2 :</span><span class="sxs-lookup"><span data-stu-id="727ba-139">On the SQL2 database, create the following new login:</span></span>  
  
    -   <span data-ttu-id="727ba-140">ORCH\SSOAdminGroup</span><span class="sxs-lookup"><span data-stu-id="727ba-140">ORCH\SSOAdminGroup</span></span>  
  
14. <span data-ttu-id="727ba-141">Installez le serveur de secret principal comme suit :</span><span class="sxs-lookup"><span data-stu-id="727ba-141">Install the Master Secret Server as follows:</span></span>  
  
    -   <span data-ttu-id="727ba-142">Ouvrez une session sur NTS5 à l'aide de ORCH\TestAdmin.</span><span class="sxs-lookup"><span data-stu-id="727ba-142">Log on to NTS5 using ORCH\TestAdmin.</span></span>  
  
    -   <span data-ttu-id="727ba-143">Installez l'authentification unique de l'entreprise en utilisant SQL2 en tant que serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="727ba-143">Install ESSO, using SQL2 as the Master Secret Server.</span></span>  
  
15. <span data-ttu-id="727ba-144">Ouvrez une session sur HIS1 à l'aide de ORCH\TestAdmin, puis installez l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="727ba-144">Log onto HIS1 using ORCH\TestAdmin, and install Enterprise Single Sign-On.</span></span> <span data-ttu-id="727ba-145">Configurez l'authentification unique de l'entreprise en tant qu'ajout SSO à HIS2 en utilisant le nom du serveur de base de données SQL2.</span><span class="sxs-lookup"><span data-stu-id="727ba-145">Configure ESSO as SSO join HIS2, using database server name SQL2.</span></span>  
  
16. <span data-ttu-id="727ba-146">Installez l'utilitaire d'administration de l'authentification unique de l'entreprise sur HIS3 à l'aide de ORCH\TestAdmin.</span><span class="sxs-lookup"><span data-stu-id="727ba-146">Install the Enterprise Single Sign-On Admin utility on HIS3 using ORCH\TestAdmin.</span></span>  
  
17. <span data-ttu-id="727ba-147">Ajoutez les utilisateurs suivants aux groupes suivants :</span><span class="sxs-lookup"><span data-stu-id="727ba-147">Add the following users to the following groups:</span></span>  
  
    -   <span data-ttu-id="727ba-148">Ajoutez ORCH\TestAppUser à ORCH\SSOAdminGroup.</span><span class="sxs-lookup"><span data-stu-id="727ba-148">Add ORCH\TestAppUser to ORCH\SSOAdminGroup</span></span>  
  
    -   <span data-ttu-id="727ba-149">Ajoutez ORCH\AffAppUser à ORCH\TestAffUserGroup.</span><span class="sxs-lookup"><span data-stu-id="727ba-149">Add ORCH\AffAppUser to ORCH\TestAffUserGroup</span></span>  
  
18. <span data-ttu-id="727ba-150">Installez SQL Server Enterprise Edition sur HIS3, puis ajoutez le compte de connexion ORCH\AffAppUser.</span><span class="sxs-lookup"><span data-stu-id="727ba-150">Install SQL Server Enterprise Edition on HIS3, and add login ORCH\AffAppUser.</span></span>  
  
19. <span data-ttu-id="727ba-151">Sur l'ordinateur HIS1, ouvrez une invite de commandes et utilisez les commandes suivantes pour définir la délégation contrainte et la transition de protocole :</span><span class="sxs-lookup"><span data-stu-id="727ba-151">On the HIS1 computer, open a command prompt and use the following commands to set constrain delegation and protocol transition:</span></span>  
  
    -   <span data-ttu-id="727ba-152">**setspn-a MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**</span><span class="sxs-lookup"><span data-stu-id="727ba-152">**setspn -A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**</span></span>  
  
    -   <span data-ttu-id="727ba-153">**setspn-a MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**</span><span class="sxs-lookup"><span data-stu-id="727ba-153">**setspn -A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**</span></span>  
  
20. <span data-ttu-id="727ba-154">Sur le **ORCH\SSOSvcUser** et **ORCH\TestAppUser** pages de propriétés, définissez la délégation appropriée pour les deux comptes d’utilisateur en sélectionnant les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="727ba-154">On the **ORCH\SSOSvcUser** and **ORCH\TestAppUser** property pages, set the proper delegation for both user accounts by selecting the following options:</span></span>  
  
    -   <span data-ttu-id="727ba-155">**N’approuver cet utilisateur pour la délégation aux services spécifiés uniquement**</span><span class="sxs-lookup"><span data-stu-id="727ba-155">**Trust this user for delegation to specified services only**</span></span>  
  
    -   <span data-ttu-id="727ba-156">**Utiliser tout protocole d’authentification**</span><span class="sxs-lookup"><span data-stu-id="727ba-156">**Use any authentication protocol**</span></span>  
  
21. <span data-ttu-id="727ba-157">À l'aide de ORCH\TestAdmin sur l'ordinateur HIS1, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="727ba-157">Using ORCH\TestAdmin on the HIS1 computer, perform the following:</span></span>  
  
    -   <span data-ttu-id="727ba-158">Ajoutez ORCH\TestAppUser au groupe d'utilisateurs du bureau distant.</span><span class="sxs-lookup"><span data-stu-id="727ba-158">Add ORCH\TestAppUser to Remote Desktop User Group</span></span>  
  
    -   <span data-ttu-id="727ba-159">Grant **emprunter l’identité d’une fois authentifié** privilège à orch\ssosvcuser.</span><span class="sxs-lookup"><span data-stu-id="727ba-159">Grant **Impersonate after authenticated** privilege to ORCH\SSOSvcUser</span></span>  
  
    -   <span data-ttu-id="727ba-160">Grant **emprunter l’identité d’une fois authentifié** privilège à orch\testappuser.</span><span class="sxs-lookup"><span data-stu-id="727ba-160">Grant **Impersonate after authenticated** privilege to ORCH\TestAppUser</span></span>  
  
22. <span data-ttu-id="727ba-161">Vérifiez votre déploiement en ouvrant une session sur HIS1 à l'aide de ORCH\TestAppUser et en exécutant la configuration d'application suivante :</span><span class="sxs-lookup"><span data-stu-id="727ba-161">Verify your deployment by logging onto HIS1 using ORCH\TestAppUser and running the following application configuration:</span></span>  
  
     <span data-ttu-id="727ba-162">Exécutez le test LogonExternalUser.</span><span class="sxs-lookup"><span data-stu-id="727ba-162">Run LogonExternalUser Test.</span></span>  
  
    ```  
    <SSO>  
       <application name="TestApp">  
          <description>An SSO Test Affiliate Application</description>  
          <contact>AffAppUser@ESSOV2.EBiz.Com</contact>  
          <appUserAccount>ORCH\TestAffAdminGroup</appUserAccount>  
          <appAdminAccount>ORCH\TestAffUserGroup</appAdminAccount>  
          <field ordinal="0" label="User ID" masked="no" />  
          <field ordinal="1" label="Password" masked="yes" />  
          <flags   
             groupApp="no"   
             configStoreApp="no"   
             allowTickets="no"   
             validateTickets="yes"   
             allowLocalGroups="yes"   
             ticketTimeout="yes"   
             adminGroupSame="no"   
             enableApp="yes"   
             hostInitiatedSSO="yes"   
             validatePassword="yes"/>  
       </application>  
    </SSO>  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="727ba-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="727ba-163">See Also</span></span>  
 [<span data-ttu-id="727ba-164">Vue d’ensemble du déploiement de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="727ba-164">SSO Deployment Overview</span></span>](../core/sso-deployment-overview.md)