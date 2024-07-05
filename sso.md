# SSO

## what is it?
Single Sign on. This is a method to allow a user to access subscribed-to content on website B via website A. The user only needs to login once - to website A - and not twice in order to access the content on B.

## SSO on Edify
Edify now seems to support SSO but it needs to be set up through Ingenta. 

### my tests

<img width="398" alt="image" src="https://github.com/AmsterdamUniversityPress/content-loading/assets/4679906/b6b2323c-c757-49d0-ba67-20f366b1d715">

 
1. go to `https://qa.aup-online.com/` 
2. login to the site with the basic authentication. (This is just to the site; you’re not logged in as a particular user)
3. go to `https://qa.aup-online.com/keycloak/out.action?signInTarget=%2F`
4. the URL changes to `https://pf.tst.legalintelligence.com/as/authorization.oauth2?response_type=code&client_id=cffe51714602a3b1fa4101080387abd6d6dcc023d91cc6171def7eb9cdd551d6&redirect_uri=https%3A%2F%2Fqa.aup-online.com%2Fsession%2Fkeycloak&scope=openid%20profile%20email&state=%2F` (or similar?)
5. log in with the test credentials
6. you now have access to the AUP site… The profile tells you you are logged in as `CMS Ingenta`
 
This login method is only necessary once. The next time you go to `https://qa.aup-online.com/keycloak/out.action?signInTarget=%2F`, you should immediately have access to the QA site. This is because a cookie has been set. (You can test this by login in via an incognito window).

(Also, this test set-up only works when your IP adres is whitelisted by LI. This is the case for AUP). 

## content
`CMS Ingenta` is a member of the group `SSO ssouser` and inherits all permissions from the group. As group members, all users have access to the same content: the content to which the group subscribes. In addition, a user may have other subscriptions.

Remember we are still talking about individual users (persons or institutions) coming into Edify via the third-party website. So that is why they belong to a group.

To add content to a group, login as site admin. Then, add content to the group. The members should now have access to that content. Note that this content is **not** listed in their "list of licenses" as the site admin sees irt. However, when the user logs in and looks under `Subscribed titles` in `My Profile`, they **do** see the content listed there.

Note that is there is a need to give different group members access to different content, then the third-party site should indicate what that content should be (i.e. what the licenses are). Edify will then automatically st up the right access. I quote Ingenta's dev team:

>  If the requirement was for each LI user to have their own separate authorisation list, then we would typically expect that list to come in via the SSO response from LI so that the system can automatically create the necessary authorisation licence records for each user when they log in via LI SSO.


## new SSO connections
How to set one up? Still an open question. it will require Ingenta's help. Again I quote Ingenta's dev team:

> If you need to have a separate SSO setup to someone other than LI, then we would configure the system so that it would create another parent group for that SSO system. 
