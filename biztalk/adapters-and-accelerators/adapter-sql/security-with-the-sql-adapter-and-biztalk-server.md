---
title: "La sécurité avec l’adaptateur SQL et BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc439d65-1d7e-4e6e-bb0d-a8cb9f0607b8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0bc410a651c179daf43c47fb573d1772f6c1e01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-sql-adapter-and-biztalk-server"></a>Sécurité avec l’adaptateur SQL et BizTalk Server
Lorsque vous configurez un port d’envoi ou un port de réception (emplacement) à l’aide de l’Administration de BizTalk Server de la console ou utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir les informations d’identification pour la base de données SQL Server. Il est important de fournir ces informations d’identification de manière sécurisée pour aider à les empêcher d’accessibles à d’acteurs potentiellement malveillants. Cette rubrique explique comment fournir plus de manière sécurisée les informations d’identification pour le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] pour les solutions BizTalk Server.  
  
 Une description plus générale de la sécurité dans le cadre de solutions BizTalk est un sujet vaste et dépasse le cadre de cette documentation. Pour savoir comment vous pouvez sécuriser vos solutions BizTalk, consultez [sécurisé et protéger vos messages BizTalk](../../core/secure-and-protect-your-biztalk-messages.md).
  
## <a name="how-do-i-protect-credentials-when-i-use-the-consume-adapter-service-biztalk-project-add-in"></a>Comment protéger informations d’identification lorsque vous utilisez le Consume Adapter Service BizTalk Project Add-in ?  
 Lorsque vous utilisez la [!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir le nom d’utilisateur et un mot de passe à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pas vous permettra de définir les informations d’identification le **configurer un URI** champ. Cela améliore la sécurité en empêchant les informations d’identification d’apparaître en texte clair. Pour plus d’informations sur la façon de récupérer des schémas de message à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour la base de données SQL Server, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## <a name="how-do-i-protect-credentials-when-i-configure-a-send-port-or-a-receive-location"></a>Comment protéger les informations d’identification lorsque vous configurez un Port d’envoi ou un emplacement de réception ?  
 Les solutions BizTalk utilisent l’adaptateur Microsoft BizTalk WCF-Custom pour utiliser les services WCF. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est une liaison WCF personnalisée qui permet aux clients d’utiliser la base de données SQL Server comme s’il s’agissait d’un service WCF. Les solutions BizTalk consomment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] via les ports d’envoi et emplacements de réception qui sont configurés pour utiliser l’adaptateur WCF-Custom. L’adaptateur WCF-Custom est, à son tour, configuré pour utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] comme type de transport. Pour plus d’informations sur la configuration des ports d’envoi et réception de ports (emplacements de réception), y compris comment configurer l’adaptateur WCF-Custom, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
 Vous configurez les informations d’identification de la base de données SQL Server à partir de la **informations d’identification** onglet de la **propriétés du Transport WCF-Custom** boîte de dialogue pour les ports d’envoi ou de la **autres** onglet de le **propriétés du Transport WCF-Custom** boîte de dialogue pour les emplacements de réception. Étant donné que l’adaptateur WCF-Custom prend en charge Enterprise Single Sign-On (SSO), vous pouvez également choisir de fournir un nom d’utilisateur et mot de passe ou une application associée SSO sur un de ces onglets. Les rubriques suivantes abordent les deux options.  
  
### <a name="user-name-password-credentials"></a>Informations d’identification de mot de passe utilisateur  
 Vous ne devez fournir un nom d’utilisateur et un mot de passe à partir de la **informations d’identification** onglet (pour les ports d’envoi) ou le **autres** onglet (pour les emplacements de réception) dans le **propriétés du Transport WCF-Custom**boîte de dialogue. Cela offre les avantages suivants :  
  
-   Vos informations d’identification ne s’affichera pas dans le **adresse (URI)** champ de la boîte de dialogue. Ainsi, ceux qui ont accès à l’écran (ou qui disposent des autorisations leur permettant d’afficher le port d’envoi ou de propriétés de l’emplacement de réception) de voir vos informations d’identification.  
  
-   Votre mot de passe n’est pas être écrite dans le fichier de liaison si vous exportez le port d’envoi ou de liaison de port de réception. Cela empêche toute personne ayant accès au fichier à partir de l’affichage de votre mot de passe.  
  
### <a name="enterprise-single-sign-on-and-sso-affiliate-applications"></a>Enterprise Single Sign-On et l’authentification unique des Applications associées  
 Vous pouvez configurer l’adaptateur WCF-Custom afin qu’il utilise l’authentification unique de l’entreprise (SSO) pour obtenir les informations d’identification pour la base de données SQL Server. L’authentification unique utilise une base de données et un secret pour chiffrer et stocker les informations d’identification de l’utilisateur. Il fournit également des services pour mapper les comptes Microsoft Windows aux informations d’identification secondaires qui sont utilisées pour accéder à un système principal. À l’aide de l’authentification unique, vous pouvez mapper un compte Windows à un nom d’utilisateur et un mot de passe sur la base de données SQL Server.  
  
 L’authentification unique utilise *applications associées* et *mappages SSO* pour mapper les informations d’identification pour le système principal. Une application associée est une entité logique dans l’authentification unique qui fait référence à un système ou une application qui nécessite des informations d’identification secondaires. Un mappage de l’authentification unique est associé à une application associée. Il est mappé à un compte Windows pour les informations d’identification secondaires utilisées par ce compte pour accéder à l’application ou le système associé. Un mappage de l’authentification unique peut être associé à un compte d’utilisateur Windows ou à un groupe.  
  
 Pour utiliser l’authentification unique avec la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez procédez comme suit.  
  
1.  Créer une application associée dans l’authentification unique pour stocker des informations d’identification de mot de passe pour la base de données SQL Server de l’utilisateur. Cette étape est souvent effectuée par une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
2.  Créez un utilisateur ou un mappage de groupe pour l’application associée qui mappe votre compte Windows pour le nom d’utilisateur et un mot de passe qui sont utilisées pour établir une connexion avec la base de données SQL Server. Selon votre installation, un utilisateur peut être en mesure d’effectuer cette étape, ou il peut nécessiter une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
> [!NOTE]
>  Lorsque configuré pour l’authentification unique, l’adaptateur WCF-Custom utilise les services fournis par l’authentification unique pour obtenir le nom d’utilisateur SQL Server et le mot de passe à partir de la base de données SSO. Il fournit ces (non chiffré) à la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], de sorte que l’adaptateur peut ouvrir une connexion à la base de données SQL Server. SSO ne fournit aucun chiffrement ou la protection via la connexion entre le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et la base de données SQL Server.  
  
 Pour plus d’informations sur l’utilisation de l’authentification unique, notamment des informations sur la création d’applications associées et les mappages de l’authentification unique, consultez [à l’aide de l’authentification unique](../../core/using-sso.md). Pour plus d’informations sur l’authentification unique, consultez [implémentation Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md).
  
## <a name="the-acceptcredentialsinuri-binding-property"></a>La propriété de liaison AcceptCredentialsInUri  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge **AcceptCredentialsInUri** propriété de liaison. Informations d’identification ne sont jamais autorisées dans l’URI de connexion.  
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[Meilleures pratiques pour sécuriser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)