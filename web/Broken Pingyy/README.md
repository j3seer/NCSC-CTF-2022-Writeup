# Challenge description

I've developed a simple web app to ping any IP/domain but i had some problems in my code .. I'm a newbie web developer so i'll give the source code to help me. flag location => /flag Link: http://20.119.58.135:789/

**Author: MONT4**

-----------------------------------------------------------

We were presented by this webpage that allows us to ping other webpages but
the website seems like its not working 

img

i tried to get command injection using just **ls** or **; ls**  but nothing works

Looking through the provided source code we can see that there's a typo in the ping command 
notice the **'** before **ping**

img

so now we just need to add a **'** before anything we type and we have to add **;** to close out the first command 
so our payload becomes 

``` ' ; ls ```

img

but we still don't get anything ! well that's because the flag is at /flag so we just need to **cat** that

Payload becomes :

``` ' ; cat /flag ```

there's our flag :

``` Securinets{Be_c4refuL_fr0m_C0mmand_1njection!!} ```