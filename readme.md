HiveSigner Helper by @fbslo

---

To start using HiveSigner, you will need HIVE account. You can create it yourself or get one on https://signup.hive.io

First, use this account as HiveSigner app: https://hivesigner.com/developers (use production mode, NOT sandbox!)

Then authorize @hivesigner for your new app account: https://hivesigner.com/authorize/hivesigner. If you don't do this, you will get error:

`unauthorized_client` `Broadcaster account doesn't have permission to broadcast for [your app]`

Your app is now ready!

---

To use helper file, include `hivesigner-helper.js` into your html file.

```
<script src="https://cdn.jsdelivr.net/npm/hivesigner"></script>
<script src="hivesigner-helper.js"></script>
```

Edit the file and repace app, callbackURL and scope.

```
const client = new hivesigner.Client({
  app: 'fbslo-b',
  callbackURL: 'http://localhost:8080',
  scope: ['vote', 'comment']
});
```

---

***There is 13 functions available:***

---

`hs_helper_login()`

Login function will redirect user to HiveSigner.com and than back to callback URL. Every time site is reloaded, it will check URL for `access_token` parameter and save it to local storage and set it as access token.

---

`hs_helper_logout()`

Logout will revoke access token and delete it from local storage.

---

`hs_helper_get_user_details()`

It will get details about current user in JSON object:

```
{
  account: { id: some_id, name: "account_name", ...},
  name: "account_name",
  scope: ["vote"],
  user: "account_nme",
  _id: "account_name"
}
```

---

`hs_helper_vote(voter, author, permlink, weight)`

100% vote is 10000 weight.

---


`hs_helper_comment(parentAuthor, parentPermlink, author, permlink, title, body, jsonMetadata)`

---

`hs_helper_delete_comment(author, permlink)`

---

`hs_helper_custom_json(requiredAuths, requiredPostingAuths, id, json)`

requiredAuths can be [], requiredPostingAuths is ["account_name"]

---

`hs_helper_transfer(to, amount, memo)`

Amount format is 1.000 HIVE (3 decimals, HIVE or HBD)

---

`hs_helper_reblog(account, author, permlink)`

---

`hs_helper_follow(follower, following)`

---

`hs_helper_unfollow(unfollower, unfollowing)`

---


`hs_helper_ignore(follower, following)`

Follower is user, following is ignored user

---

`hs_helper_claim_balance(account, rewardHive, rewardHbd, rewardVests)`

rewardHive/rewardHbd format is same as for transfer (3 decimals, HIVE or HBD), rewardVests format is 1.000000 VESTS (6 decimals)


---

If you find this helper useful, donations are welcome:
* Hive/Steem: @fbslo
