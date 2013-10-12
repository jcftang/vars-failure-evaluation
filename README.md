This fails with ansible on commit 8faaae142ce84ae8029520c4d0a4cc343bbc9070

The example in this repo works with ansible 1.3.2, so this failure appears to be a regression


    $ ansible-playbook test.yml 

    PLAY [compute_frontend] ******************************************************* 

    GATHERING FACTS *************************************************************** 
    ok: [192.168.252.100]

    TASK: [test | shell [ -f /tmp/done_this ] && echo 'done' || echo ''] ********** 
    fatal: [192.168.252.100] => error while evaluating conditional: {% if result.stdout.find('done') == -1 %} True {% else %} False {% endif %}

    FATAL: all hosts have already failed -- aborting

    PLAY RECAP ******************************************************************** 
               to retry, use: --limit @/home/jtang/test.retry

    192.168.252.100            : ok=1    changed=0    unreachable=1    failed=0  



