# Challenge description

I've developed a simple web app to ping any IP/domain but i had some problems in my code .. I'm a newbie web developer so i'll give the source code to help me. flag location => /flag Link: http://20.119.58.135:789/

**Author: MONT4**

-----------------------------------------------------------

We were presented by this webpage that allows us to ping other webpages but
the website seems like its not working 

![3](https://user-images.githubusercontent.com/58823465/151815537-56958a35-7b1c-43a9-9c9b-9228a8364c00.png)


i tried to get command injection using just **ls** or **; ls**  but nothing works

Looking through the provided source code we can see that there's a typo in the ping command 
notice the **'** before **ping**

![image](https://user-images.githubusercontent.com/58823465/151815670-63d7d1e3-8365-4d4b-99ab-702601011a64.png)


so now we just need to add a **'** before anything we type and we have to add **;** to close out the first command 
so our payload becomes 

``` ' ; ls ```

![image](https://user-images.githubusercontent.com/58823465/151815731-b4e9f0a4-02c3-47fe-8c8a-f56aa89002c3.png)

but we still don't get anything ! well that's because the flag is at /flag so we just need to **cat** that

Payload becomes :

``` ' ; cat /flag ```

![image](https://user-images.githubusercontent.com/58823465/151815784-28939afe-9880-4945-a4dc-a28a1fd65335.png)


there's our flag :

``` Securinets{Be_c4refuL_fr0m_C0mmand_1njection!!} ```
