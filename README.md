MailChimp Synchronisation for ProcessWire
=========================================

This prototype module will synchronise your [ProcessWire](http://processwire.com/) user list with a list in MailChimp. It takes the approach of [synchronising the entire user list into a single list](http://apidocs.mailchimp.com/api/how-to/sync-you-to-mailchimp.php) but stores the user's roles as _Interests_. This allows you to segment your users based on their group membership and avoids the challenges of adding and removing users onto multiple lists.

Installation and use
--------------------

Currently the module will not automatically update a new list. To install the module you will need to do the following:

1. Create an API key and a blank list in MailChimp
2. Make sure you have email, first name and surname fields, or equivalent in your user database in PW
3. Add your key and the field names in the module setup
4. From a template run, `$modules->get('MailChimpSync')->syncAll($users);` to do the initial import. You can also run this from an interactive shell by loading the PW api and using the following, `wire('modules')->get('MailChimpSync')->syncAll(wire('users));`

From now on whenever one of the synchronised fields is changed, the user's details will be updated on MailChimp. You can [segment your list](http://mailchimp.com/features/segmentation-and-groups/) based on the user's [role membership](http://processwire.com/api/user-access/roles/).

Further improvements
--------------------

* Switch to scheduled updates. To avoid updating the whole list user's could be flagged as requiring an update when one of the relevant fields is updated. LazyCron or regular cron jobs would update these users on the list.
* Automatic creation of the list on MailCimp and initial import.