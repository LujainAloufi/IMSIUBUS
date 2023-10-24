# IMSIUBUS
IMSIU Transportation System Project
import { authentication } from 'wix-members-frontend';
$w.onReady(function () {

            const loginMember = async () => {

                const username = $w("#username").value;
                const password = $w("#password").value;
                try {
                    const memberIsLoggedIn = await authentication.login(username, password)
                    console.log(memberIsLoggedIn);
                   
                } catch (error) {
                    console.log(error);
                    $w("#errorMessage").text = "There was an error plaese t ry agein";
                    $w("#errorMessage").show();
                }
            }
            $w("#Signin").onClick(loginMember);




            });
