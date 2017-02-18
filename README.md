###HOW TO
1. Set up a vlan counter, cryptomap counter and a parent subnet

  ``` ansible-playbook test-nsot.yaml  --tags "setup" ```

2. Run the playbook as many times as you please to generate and
   allocate different iterables

  ```ansible-playbook test-nsot.yaml -e "site_id=1 bu_name=ab" --tags "play"
     ansible-playbook test-nsot.yaml -e "site_id=1 bu_name=ab" --tags "play"
     ansible-playbook test-nsot.yaml -e "site_id=1 bu_name=xyz" --tags "play" ```

3. Perform a DELETE operation in lieu of a "playbook revert" to free
   up the previously allocated iterables in the backend, using the
   friendly tag used to create them

  ``` ansible-playbook test-nsot.yaml -e "site_id=1 bu_name=ab" --tags
 "local_cleanup" ```

 >> Cleans up all the subnets and iterables used by all runs of "ab"

  ``` ansible-playbook test-nsot.yaml -e "site_id=1 bu_name=xyz"
 --tags "local_cleanup" ```

 >> Cleans up all the subnets and iterables used by all runs of "ab"

4. Revert NSoT to the blank state - remove the vlan, cryptomap and
   parent subnet that was used in the demo

  ``` ansible-playbook test-nsot.yaml -e "site_id=1 bu_name=aa" --tags "cleanup"```
