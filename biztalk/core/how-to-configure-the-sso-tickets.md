---
title: Comment configurer les Tickets SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], configuring tickets
- SSO, tickets
- tickets [SSO], configuring
ms.assetid: 32f0384b-ac79-4cce-b3f5-f4f8a73a673a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef78c47c3da88945573a70e85580c90e05b1d225
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-sso-tickets"></a><span data-ttu-id="3387d-102">Comment configurer les Tickets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3387d-102">How to Configure the SSO Tickets</span></span>
<span data-ttu-id="3387d-103">Vous pouvez utiliser le composant logiciel enfichable MMC ou la ligne de commande pour contrôler entièrement le comportement de ticket du système d'authentification unique, y compris l'autorisation des tickets et leur validation par le système.</span><span class="sxs-lookup"><span data-stu-id="3387d-103">You can use the MMC Snap-In or the command line to control ticket behavior for the entire Single Sign-On system, including whether to allow tickets, and whether the system must validate the tickets.</span></span>  
  
 <span data-ttu-id="3387d-104">Vous pouvez utiliser Yes, No, On ou Off pour indiquer s’il faut autoriser ou de valider des tickets.</span><span class="sxs-lookup"><span data-stu-id="3387d-104">You can use Yes, No, On, or Off to indicate whether to allow and/or validate tickets.</span></span> <span data-ttu-id="3387d-105">Ces mots, dont la casse est indifférente, doivent être utilisés indépendamment de vos paramètres de langue.</span><span class="sxs-lookup"><span data-stu-id="3387d-105">These words are case independent, and must be used regardless of your language settings.</span></span>  
  
 <span data-ttu-id="3387d-106">Si la fonctionnalité Administration de l'authentification unique est installée sur un ordinateur distant, une opération IssueTicket peut être effectuée à distance.</span><span class="sxs-lookup"><span data-stu-id="3387d-106">If you have the SSO Administration feature installed on a remote computer, remote IssueTicket operation can be performed.</span></span> <span data-ttu-id="3387d-107">Notez que tout le trafic entre le module Administration de l'authentification unique et le module Moteur d'exécution (service ENTSSO) est chiffré.</span><span class="sxs-lookup"><span data-stu-id="3387d-107">Note that all traffic between the SSO Administration module and the Runtime module (ENTSSO service) is encrypted.</span></span>  
  
 <span data-ttu-id="3387d-108">L'utilitaire de ligne de commande ssomanage.exe permet de spécifier le délai d'expiration du ticket au niveau de l'application associée uniquement lors de la mise à jour de l'application, pas lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="3387d-108">Using the command line utility, ssomanage.exe, you can specify the ticket timeout at the Affiliate Application level only when an update of the Application is performed,  not at creation time.</span></span>  
  
 <span data-ttu-id="3387d-109">Seul un administrateur de l’authentification unique peut configurer des tickets au niveau du système d’authentification unique et au niveau de l’Application associée.</span><span class="sxs-lookup"><span data-stu-id="3387d-109">Only an SSO Administrator can configure tickets at the SSO System level and at the Affiliate Application level.</span></span>  
  
 <span data-ttu-id="3387d-110">Si les tickets sont désactivés au niveau du système, ils ne peuvent pas être utilisés non plus au niveau de l'application associée.</span><span class="sxs-lookup"><span data-stu-id="3387d-110">If ticketing is disabled at the system level, it cannot be used at the Affiliate Application level either.</span></span> <span data-ttu-id="3387d-111">Il est possible d’activer les tickets au niveau du système et de désactiver au niveau de l’Application associée.</span><span class="sxs-lookup"><span data-stu-id="3387d-111">It is possible to enable tickets at the system level and disable it at the Affiliate Application level.</span></span>  
  
 <span data-ttu-id="3387d-112">Si la validation des tickets est activée au niveau du système, elle est également obligatoire au niveau de l'application associée.</span><span class="sxs-lookup"><span data-stu-id="3387d-112">If validation is enabled at the system level, validation of tickets are required at the Affiliate Application level as well.</span></span> <span data-ttu-id="3387d-113">Il est possible de désactiver la validation des tickets au niveau du système et de l'activer au niveau de l'application associée.</span><span class="sxs-lookup"><span data-stu-id="3387d-113">It is possible to disable validation at the system level and enable it at the Affiliate Application level.</span></span>  
  
 <span data-ttu-id="3387d-114">Si un délai d'expiration du ticket est spécifié tant au niveau du système qu'au niveau de l'application associée, c'est celui qui est défini au niveau de l'application associée qui est utilisé pour déterminer la durée d'expiration du ticket.</span><span class="sxs-lookup"><span data-stu-id="3387d-114">If Ticket timeout is specified both at the System level and the Affiliate Application level, the one specified at the Affiliate Application level is used to determine the ticket expiry time.</span></span>  
  
 <span data-ttu-id="3387d-115">Pour plus d’informations sur les tickets et leur validation, consultez [Tickets SSO](../core/sso-tickets.md).</span><span class="sxs-lookup"><span data-stu-id="3387d-115">For more information about tickets and tickets validation, see [SSO Tickets](../core/sso-tickets.md).</span></span>  
  
### <a name="to-configure-the-enterprise-single-sign-on-tickets-using-the-mmc-snap-in-for-the-affiliate-application"></a><span data-ttu-id="3387d-116">Pour configurer les tickets d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC pour l'application associée</span><span class="sxs-lookup"><span data-stu-id="3387d-116">To configure the Enterprise Single Sign-On tickets using the MMC Snap-In for the Affiliate Application</span></span>  
  
1.  <span data-ttu-id="3387d-117">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="3387d-117">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="3387d-118">Dans le volet d’étendue d’enfichable MMC ENTSSO, développez le **Applications associées** nœud.</span><span class="sxs-lookup"><span data-stu-id="3387d-118">In the scope pane of the ENTSSO MMC Snap-In, expand the **Affiliate Applications** node.</span></span>  
  
3.  <span data-ttu-id="3387d-119">Avec le bouton droit **Application associée**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3387d-119">Right-click **Affiliate Application**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3387d-120">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="3387d-120">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="3387d-121">Sélectionnez **autoriser les Tickets** et configurez le délai d’attente du ticket comme il convient.</span><span class="sxs-lookup"><span data-stu-id="3387d-121">Select **Allow Tickets** and configure the ticket timeout as appropriate.</span></span>  
  
### <a name="to-configure-the-enterprise-single-sign-on-system-level-tickets-using-the-command-line"></a><span data-ttu-id="3387d-122">Pour configurer les tickets au niveau système d'authentification unique de l'entreprise à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="3387d-122">To configure the Enterprise Single Sign-On system-level tickets using the command line</span></span>  
  
1.  <span data-ttu-id="3387d-123">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="3387d-123">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="3387d-124">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="3387d-124">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="3387d-125">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="3387d-125">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="3387d-126">Type **ssomanage – tickets \<autorisée Oui/non >  *\<valider oui/non >***, où  *\<autorisée Oui/non >* Indique si les tickets seront autorisés ou non, et  *\<valider oui/non >* indique si les tickets devront être validés après leur échange.</span><span class="sxs-lookup"><span data-stu-id="3387d-126">Type **ssomanage –tickets \<allowed yes/no> *\<validate yes/no>***, where *\<allowed yes/no>* indicates whether tickets will be allowed or not, and *\<validate yes/no>* indicates whether tickets will need to be validated after they are redeemed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3387d-127">Vous pouvez utiliser les mots Yes, No, On ou Off pour indiquer s'il convient d'autoriser ou de valider des tickets.</span><span class="sxs-lookup"><span data-stu-id="3387d-127">You can use yes, no, on, or off to indicate whether to allow and/or validate tickets.</span></span> <span data-ttu-id="3387d-128">Ces mots, dont la casse est indifférente, doivent être utilisés indépendamment de vos paramètres de langue.</span><span class="sxs-lookup"><span data-stu-id="3387d-128">These words are case independent, and must be used regardless of your language settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3387d-129">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="3387d-129">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3387d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3387d-130">See Also</span></span>  
 <span data-ttu-id="3387d-131">[Présentation de l’authentification unique](../core/understanding-sso.md) </span><span class="sxs-lookup"><span data-stu-id="3387d-131">[Understanding SSO](../core/understanding-sso.md) </span></span>  
 [<span data-ttu-id="3387d-132">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3387d-132">Using SSO</span></span>](../core/using-sso.md)