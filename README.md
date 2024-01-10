# 3-tier_AWS_Project
# Hosting a static website on AWS S3 using CloudFront

## Tier 1 FOUNDATION :

### Scenario Part 1:
#### Our Website is an imaginary fintech startup that provides banking services to its clients. The main channel for acquiring new customers and facilitating interaction with the bank is the company’s website. Presently, the website is hosted on a server located on-premises, necessitating an IT team exclusively dedicated to its management and upkeep. This arrangement incurs supplementary expenses for the company and introduces an extra layer of intricacy to the infrastructure.

  ### To address these challenges, Our Bank Website has decided to move its website to AWS S3. The change would provide the following benefits :
### Cost Savings, Improved Scalability, High Availability and reduced management overhead.

### Scenario Part 2:
#### Our Website is experiencing a growing customer base accessing their website from various locations worldwide. Consequently, the website’s performance is deteriorating due to latency problems. Furthermore, the bank is concerned about safeguarding the website against cyber attacks. Additionally, Level Up Bank aims to reduce hosting expenses while simultaneously enhancing website performance and security.

  ### To overcome these challenges, I recommend that Level Up Bank integrate AWS CloudFront into their S3 Hosted Static website. AWS CloudFront is a content delivery network (CDN) service that efficiently distributes static and dynamic web content, including HTML, CSS, JavaScript, images, and videos, to global users, ensuring minimal latency and rapid data transfer speeds. The benefits of this strategy are as follows:

### Improved website performance, enhanced website security and reduced website hosting costs.

# Project Overview : This project has 3 tiers of difficulty. 
## - Foundational 
## - Advanced 
## - Complex 
##### I will be challenging myself to complete all 3 tiers and will be breaking down each tier’s goals and steps.

# The goals for this tier are:
— Create an S3 bucket using the AWS console and upload the index.html file.

— Modify the S3 bucket so that it can host a static website and can be reachable through the internet

— Verify internet access using the bucket website endpoint and not the object URL

# Step 1: Create s3 bucket in your aws acc. with versioning enables and public facing bucket

![1](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/7bee6b9e-95be-4371-9353-f08e96f36a6d)


# Step 2: Upload index.html and all its necessary files in the bucket with all folder content in the bucket

![2](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/11cdbf6c-195b-45d7-be9c-1f6e25edbce7)


# Step 3: Grant ACL to the bucket after uploading object to the bucket

![3](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/c53e10b2-42bf-446e-a1d6-6728ddd7b7b2)

![4](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/3af8e7a6-5855-4e98-b8bd-72a467058954)


# Step 4: now goto the proper (below down) static website hosting enable it (click) edit > (check) enable > index document : index.html > save changes. 

![5](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/4572cd09-23ee-473f-93ba-f8d113bfbb68)


# Step 5: Again goto properties > static website hosting you'll see the link (url) > copy and paste in the browser 

![6](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/05216f18-a0d4-4ace-a8db-9805c7978a97)


![7](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/6e46f718-5d41-42a6-9214-a7676974c67b)


# Tier 2 Level up to Advance

## The goals for this tier are :
— Use CloudFront along with our S3 Static hosted website to take advantage of Edge Caching for better performance

— Ensure the CloudFront URL can only be accessed through HTTPS and that any HTTP traffic is redirected to HTTPS

— Verify you can reach the website using the CloudFront URL and make sure the URL redirects HTTP to HTTPS

— Verify that caching is working by making a small change to the HTML code

# Step 6:  Goto CloudFront and (click CloudFront distribution)

![8](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/08507a50-06aa-4fe7-8817-c1a955c9d6e9)

# Step 7: origin domain: (click) here you will see your bucket website > (select) it

![9](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/6a1b5a1e-61f5-4293-838e-b1bbe98e20d6)

# Step 8: Go below and in the origin access: (choose) Origin access control settings (recommended) > (click) create control settings > leave bydefault settings as it is > (click) create 

![10](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/28f82014-f5a9-4656-b1d7-9ca88dbeddd9)

![10 1](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/3822276b-fbca-4c9f-9151-5bef5f82261b)

### (Ignore the Origin access control is required message for now. This gets taken care of once you apply the bucket policy in S3)

# Step: 9 change the option to Redirect HTTP to HTTPS.

![11](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/cf71723a-41a0-4fa4-a5e5-bd7eefda5956)

![12](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/0f185bbe-224e-4fab-811d-ab3f77e49cc7)

# Step 10: Scroll down to WAF and select Do not enable security protection. (Only because this is a sandbox. In the real world we would need to add this protection. Especially for a banking website)

![13](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/df53ea13-141f-45fc-a670-b8dc6e175ba3)

# Step 11: Now Click create distribution

# Step 12: After creation you will see message prompting about (the s3 bucket policy needs to be updated) > (click) copy policy

![14](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/6b8cc664-8398-40b7-9eb1-769074a10976)

# Step 13: Open s3 resource in another tab > go to permissions for your website bucket > In the Bucket policy section > (click) on Edit. Then paste the policy > (click) on Save changes.

![15](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/5d470853-80ca-4473-97f8-fe32471cab90)

![16](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/d4b85041-ebff-4aba-a40f-5eee2b76999c)


# Step 14: Now go back to our CloudFront distribution > (click) distribution > you will see the status is displaying Enabled before you continue.

![17](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/c29642f3-371c-4c1c-9ddd-b66534360efc)

## (click) your distribution Id > settings > (click) edit > Scroll down to Default root object and type in index.html then save the changes.

![18](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/263fd750-3cee-4a8b-9b8b-e5779e0e41c9)

## goto to the distribution and copy the distribution domain name and paste in the incognito tab > There you will see your website. 

![19](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/daa9ccb6-e168-4f9f-b8f3-65d3343ba51b)


# Hence, The website is now working via CloudFront and it is using HTTPS!!!
(Now, to see if we are able to meet the redirection requirement. Click in the address bar and change the HTTPS to HTTP then hit enter. Success!!!! HTTP is being redirected to HTTPS.)

# Step 15: The last step in this tier to is verify that cache is working. 
### To test this, we will open the index.html file in VS Code > make some changes then upload the updated file into S3 > If cache is working, the object URL will show the changes but the CloudFront URL will not right away.

![20](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/d30bb0d0-475c-4a5e-9bfb-aabdf8696853)


# Step 16: I saved the file and uploaded it to S3 overwriting the existing index.html.


![21](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/f184bec7-8640-4a33-a80f-92bcd5dd1e31)

![22](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/b1806d0d-f79c-4797-bb7b-34689122d1ad)

## *Note: Overwriting the index.html file with the updated version does not keep the public permission on the file. You must manually make the file public again. This is only if you would like to view the website using the object URL. *


# Step: 17 Now viewing the website using the object URL(click on index.html > click object URL > paste in the browser) gave me this result:

![23](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/42a77b6a-1f99-4fe0-9834-f257ae1270db)


## Which means cache is working properly!!!!

## We have now satisfied all requirements for Tier 2. Time to tackle Tier 3.

# Now, Time for 3rd Tier:
# The goal for this tier is to improve security by ensuring that no end users can go around CloudFront and access the S3 bucket directly while verifying that the website is still accessible after whatever changes are made.

## We took care of some of this in tier 2 when we enabled Origin access control and applied the bucket policy in S3 which gives the bucket access to only CloudFront.

### However, we still have the bucket and index.html set to Publicly Accessible. Let’s go change that right now.

# Step 18: Go into the website S3 bucket > (click) on index.html then go to permissions > Then click on the Edit button in the Access control list section

# Step 19: Remove the Read access in the Everyone (public access) group then save the changes. This will keep users from accessing the index.html file directly from the S3 bucket.

![24](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/d3846cbf-4a15-49c9-b19f-049c8f6cbc73)


![25](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/48bca521-e969-4f09-9777-6dd4e3fd6173)

# Step 20: Go to your bucket > (click) on permissions > Then click Edit in the Block public access (bucket settings) section > Go ahead and (click) on checkbox next to Block all public access then save the changes. You will have to enter confirm in the field > then click on Confirm to be able to continue.

![26](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/050b2e51-6344-4a7b-862a-d5ce451cf121)

# You should now see that the Publicly Accessible message in your bucket is no longer there. Indicating that we are more secure right now. But let’s test it out. We should get access denied messages when using both bucket website endpoint and object URL’s. Open an incognito browser tab and test each link.

![27](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/a08f48fc-4101-4aac-ac23-d11a048f36a3)

![28](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/e4043368-bba8-4033-83a9-7e4e421ce368)

# Step 21: Now that we made the changes to secure our S3 bucket, we need to find out if any of these changes affected the website from functioning using the CloudFront URL.

# Go to the CloudFront URL and paste into an incognito tab

![29](https://github.com/sheikhnavezz/3-tier_AWS_Project/assets/134357661/aeb11fe2-d198-4fd9-a752-f506dae42c53)

## Success!!!! The website is still functional and the changes we made previously, are now available on the website.

## This concludes the first project for Level Up in Tech where we learned how to host a static website via S3 then add CloudFront for better availability, security and improved website performance because of the edge locations.
