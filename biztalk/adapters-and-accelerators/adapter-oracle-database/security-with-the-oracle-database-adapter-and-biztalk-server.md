---
title: "Sécurité avec l’adaptateur de base de données Oracle et BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user name password credentials
- SSO mapping
- credentials
- credentials, protecting
- credentials, security considerations
- affiliate application
ms.assetid: c7e0be64-4ab9-4ee3-b88a-4f8f5f07b280
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47c4ad584f23b156d2f28397952074d358995136
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-oracle-database-adapter-and-biztalk-server"></a>Sécurité avec l’adaptateur de base de données Oracle et BizTalk Server
Lorsque vous configurez un port d’envoi ou un port de réception (emplacement) à l’aide de l’Administration de BizTalk Server de la console ou utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir les informations d’identification pour la base de données Oracle. Il est important de fournir ces informations d’identification de manière sécurisée pour aider à les empêcher d’accessibles à d’acteurs potentiellement malveillants. Cette rubrique explique comment fournir plus de manière sécurisée les informations d’identification pour le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] pour les solutions BizTalk Server.  
  
 Une description plus générale de la sécurité dans le cadre de solutions BizTalk est un sujet vaste et dépasse le cadre de cette documentation. Pour savoir comment vous pouvez sécuriser vos solutions BizTalk, consultez [sécurisé et protéger vos messages BizTalk](../../core/secure-and-protect-your-biztalk-messages.md).  
  
## <a name="how-do-i-protect-credentials-when-i-use-the-consume-adapter-service-biztalk-project-add-in-or-add-adapter-metadata-wizard"></a>Comment protéger informations d’identification lorsque vous utilisez le Consume Adapter Service BizTalk Project Add-in ou l’Assistant Ajout d’adaptateur métadonnées ?  
 Lorsque vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour extraire les schémas de message pour une solution BizTalk, vous devez fournir un nom d’utilisateur et un mot de passe pour la base de données Oracle. Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. Cela garantit que vos informations d’identification ne seront pas affichées dans le **configurer un URI** champ le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] boîte de dialogue, où toute personne ayant accès à l’écran de votre ordinateur peut les lire. Pour plus d’informations sur la façon de récupérer des schémas de message à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour la base de données Oracle, consultez [obtenir les métadonnées pour des opérations Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).  
  
## <a name="how-do-i-protect-credentials-when-i-configure-a-send-port-or-a-receive-location"></a>Comment protéger les informations d’identification lorsque vous configurez un Port d’envoi ou un emplacement de réception ?  
 Les solutions BizTalk utilisent l’adaptateur Microsoft BizTalk WCF-Custom pour utiliser les services WCF. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison WCF personnalisée qui permet aux clients d’utiliser la base de données Oracle comme s’il s’agissait d’un service WCF. Consomment des solutions BizTalk le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] via les ports d’envoi et emplacements de réception qui sont configurés pour utiliser l’adaptateur WCF-Custom, qui est, à son tour, configuré pour utiliser le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] comme type de transport. Pour plus d’informations sur la configuration des ports d’envoi et réception de ports (emplacements de réception), y compris comment configurer l’adaptateur WCF-Custom, consultez [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  
  
 Vous configurez les informations d’identification de la base de données Oracle à partir de la **informations d’identification** onglet de la **propriétés du Transport WCF-Custom** boîte de dialogue pour les ports d’envoi ou de la **autres** onglet de la **Propriétés du Transport WCF-Custom** boîte de dialogue pour les emplacements de réception. Étant donné que l’adaptateur WCF-Custom prend en charge Enterprise Single Sign-On (SSO), vous pouvez choisir de fournir un nom d’utilisateur et mot de passe ou une application associée SSO sur un de ces onglets. Les rubriques suivantes abordent les deux options.  
  
### <a name="user-name-password-credentials"></a>Informations d’identification de mot de passe utilisateur  
 Vous ne devez fournir un nom d’utilisateur et un mot de passe à partir de la **informations d’identification** onglet (pour les ports d’envoi) ou le **autres** onglet (pour les emplacements de réception) dans le **propriétés du Transport WCF-Custom**boîte de dialogue. Cela offre les avantages suivants :  
  
-   Vos informations d’identification ne s’affichera pas dans le **adresse (URI)** champ de la boîte de dialogue. Ainsi, ceux qui ont accès à l’écran (ou qui disposent des autorisations leur permettant d’afficher le port d’envoi ou de propriétés de l’emplacement de réception) de voir vos informations d’identification.  
  
-   Votre mot de passe n’est pas être écrite dans le fichier de liaison si vous exportez le port d’envoi ou de liaison de port de réception. Cela empêche quiconque ayant accès au fichier à partir de l’affichage de votre mot de passe.  
  
### <a name="enterprise-single-sign-on-and-sso-affiliate-applications"></a>Enterprise Single Sign-On et l’authentification unique des Applications associées  
 Vous pouvez configurer l’adaptateur WCF-Custom pour utiliser Enterprise Single Sign-on (SSO) pour obtenir les informations d’identification pour la base de données Oracle. L’authentification unique utilise une base de données et un secret pour chiffrer et stocker les informations d’identification de l’utilisateur. Il fournit également des services pour mapper les comptes Microsoft Windows aux informations d’identification secondaires qui sont utilisées pour accéder à un système principal. À l’aide de l’authentification unique, vous pouvez mapper un compte Windows à un nom d’utilisateur et le mot de passe sur la base de données Oracle.  
  
 L’authentification unique utilise *applications associées* et *mappages SSO* pour mapper les informations d’identification pour le système principal. Une application associée est une entité logique dans l’authentification unique qui fait référence à un système ou une application qui nécessite des informations d’identification secondaires. Un mappage de l’authentification unique est associé à une application associée. Il est mappé à un compte Windows pour les informations d’identification secondaires utilisées par ce compte pour accéder à l’application ou le système associé. Un mappage de l’authentification unique peut être associé à un compte d’utilisateur Windows ou à un groupe.  
  
 Pour utiliser l’authentification unique avec la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez procédez comme suit.  
  
1.  Créer une application associée dans l’authentification unique pour stocker des informations d’identification de mot de passe pour la base de données Oracle de l’utilisateur. Cette étape est souvent effectuée par une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
2.  Créez un utilisateur ou un mappage de groupe pour l’application associée qui mappe votre compte Windows pour le nom d’utilisateur et un mot de passe qui sont utilisées pour établir une connexion avec la base de données Oracle. Selon votre installation, un utilisateur peut être en mesure d’effectuer cette étape, ou il peut nécessiter une personne disposant de types spéciaux des privilèges d’administrateur de l’authentification unique.  
  
> [!NOTE]
>  Lorsque configuré pour l’authentification unique, l’adaptateur WCF-Custom utilise les services fournis par l’authentification unique pour obtenir le nom d’utilisateur Oracle et le mot de passe à partir de la base de données SSO. Il fournit ces (non chiffré) à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], de sorte que l’adaptateur peut ouvrir une connexion à la base de données Oracle. SSO ne fournit aucun chiffrement ou la protection via la connexion entre le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et la base de données Oracle.  
  
 Pour plus d’informations sur l’utilisation de l’authentification unique, notamment des informations sur la création d’applications associées et les mappages de l’authentification unique, consultez [à l’aide de l’authentification unique](../../core/using-sso.md). Pour plus d’informations sur l’authentification unique, consultez [implémentation Enterprise Single Sign-On](../../core/implementing-enterprise-single-sign-on.md).  
  
## <a name="the-acceptcredentialsinuri-binding-property"></a>La propriété de liaison AcceptCredentialsInUri  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces le **AcceptCredentialsInUri** propriété de liaison. Cette propriété détermine si les informations d’identification de la base de données Oracle sont autorisées dans l’URI de connexion. Par défaut, **AcceptCredentialsInUri** est **false** et [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] lève une exception si les informations d’identification sont incluses dans l’URI.  
  
 Cette propriété est visible, car il existe certains scénarios de programmation qui requièrent les informations d’identification présentes dans l’URI de connexion. Il ne doit jamais être le cas lorsque vous configurez un port d’envoi ou un emplacement de réception ou lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Il est recommandé de ne pas définir **AcceptCredentialsInUri** à **true**. Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
 Le **AcceptCredentialsInUri** propriété de liaison n’est pas disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] dans les **liaison** onglet lors de la configuration de WCF-Custom WCF-OracleDB port d’envoi ou de réception. Pour définir la valeur de la **AcceptCredentialsInUri** propriété de liaison, vous devez ouvrir le fichier de liaisons de l’adaptateur (fichier XML) qui est créé une fois que vous avez généré à l’aide des métadonnées du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], puis recherchez la propriété liaison dans le fichier. Spécifiez une valeur appropriée pour cette propriété de liaison, enregistrez le fichier de liaison, puis importer le fichier de liaison dans BizTalk Server. Consultez [liaisons de l’adaptateur SQL de réutiliser](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)   
[Meilleures pratiques](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)