# C++ Controls Project README
This README will explain the major portions of this project. Primarily, the controllers.

# Body Rate Controller
The body rate controller is implemented in ***lines 111-113***. The purpose of this controller was to calculate a desired 3 axis moment when we were given a desired and current body rate (p, q, r). We can calculate the moment by subtracting the desired body rate vector by the actual body rate vector to get our error term. We multiply this error term by the gain parameter kpPQR, another vector, and multiply each term in the vector with its corresponding moment of inertia.
# Roll Pitch Controller
The roll pitch controller is implemented in ***lines 142-159***. The purpose of this controller was to calculate desired pitch and roll angle rates based on lateral acceleration, attitude and the commanded thrust. The implementation starts with an if statement where the commanded thrust is positive. When the thrust is positive, then we organize the code according with the following image.
![enter image description here](https://lh3.googleusercontent.com/rx3Q_NArqJfSYfhiwe4K3VUvlDcmfUxvcDa9SMrjYSFNsEG6IjhJRNZpkdlUP0E-K87gNWGKTMoIfblSFqrTCo3QKF2FjxzewKPvcyq4ruHPBz6mcEPvN3YrgfiRXDN04At0KeyaWoBBxm_D7CN7u2OtWaNcUTgcpNFdbTRY8XX0d8Mp369Eqjozy24156ytNbTmyNQVYsu2wslD2cuTflh0lLuPkk68FQnv6R6HRN2xVUvHIE6q0Z2a-pw0HyYkLfZeP5xUP08_b_0ZmmxbIkbMNFMBy0vB8fxKCHRKDiXpFys_SsYDCUqP2MQXK66mmviVk7fGymNNZ9KSk6jrCuIyD2QdvIZ2tB9nKwcdT-xuUf1sn8VKtQhiXtH1eHuaptS3PKjX8IhPq1J3ou5FWX_DHGUb_Hx41_WJFnSbqlCE1Nxm2zUR-H-gtkRmiqfl_veZdhUWb_Wux4DaG3YB2NiJA2O05EaSq35htX8aaWNRL2GXXN4J1m4U48DgOl4MInWVpjt_6VdFyiVso-GfqqfDdyDJPBawo18GJYj0mqbUUCeyrm9KbiWwUkhpCOQ19d5yxOa8dYD5TDjwQcb-BhI2GNgd0QQah2wvyaE_4o24wp8pyzmQOlWd6T_KeMS0Qk3suryWLyEu48u3DHn8AdHcVMN45PhlQAbzvWbtIAG7trTrkeX6FIrv_hEMZVaWig38wAONmty0rSAm5umSi8Y=w616-h174-no?authuser=0)
Where the b_c_x term in this image is the commanded rotation matrix elements. This value was constrained in the code with the max tilt angles. The rest of the calculation is as follows:
![enter image description here](https://lh3.googleusercontent.com/JNYp7jJhiZpxgGBwXUTMRajvRS2FiKA9QDbd9rax5TL_Tf--um721-szxNv_Ou6Q13xNh-X8-cwncMns3YILsMrL_vAIRmI5lPHl9eymCGGm-lvgXt4MEfN6m56OgD5WKRafAQavlSScuTv1qXYyVFrRFhQKESgVB_xUKr9tEI32TivzFqLIxfUj4WiBs-v-vy4_quSJRfk8pNNmhozSrHj8ghaCe1OLIZQmD79auE6Q5to-iZ9XL3vShjyByljDIJiCWqiWs2HxZRKANaB00L0p61yb4FnJLesMUUymDfUbi-2QERznUQSWGuhpFhvvSHPLG8rfKvirJ-kqmcnXbihO8d0_2iwjZGz4JP_hd8G50Mhst9AfaQJ2TyBLTMR4KZU5LncEHKQZ24ltkHhA9cMe28LjQuMUI6S26w8GW8JseWGqBpPu_il9Q4bUPTSg0N330B6_LiGah1djtgemLIYbQdaGX612sFpbQ4vGVhKKtBqrRGoIygHcWp8FpvLIgbdKfXSohPlbLBwyrpGIYqZNtfy_JQSg3bXrRcZvZ7xcVIHbyK-5Jc6eFJJqRz8I0i4--5B6rLZMxRf0n_oyAbbAukr70K8C1rWAxImmtEQk8Rb9K7BPlHT6Ay3pX88X_hhGMr9UuER0EsNBeg7TLKO4_6jmEHrRywvPyflrDIoppP60IEeTKZN3FKbUxYMzIgIVUfGFFPiQxlENqbOJ-aw=w268-h146-no?authuser=0)
![enter image description here](https://lh3.googleusercontent.com/QeP9IBcA02AVmxig_2ufHdD4Mo00awVdrM04R2RLy0tpSmM7p-UrN3XQlTrRJnLMBCEuzwxt58UI2DTy2Z0TyzvXlrh0ENezIzXoSayxR2MPDTs-X0I0hC1UTzghd0TpruG5YCJ7pQPRrsYAfODtIRNYmawK10rxhvhBZD1P1wUkyvMO-_2vD6xMLYiA_AnYYBjkXrXpcQ1-xSVaGkuH2-8nGOXi4ThJJHy404GUr8-xTUqX_PFBz7fl7uCHZKY2T4Eq_RW4LN51tanMBj6cAbQZC8Gy4NYCKQMyCkmSiFZ6jew-EoAL7GfeDQIETlzeASCLNpl1tlQx5zxiy_w7g5LV3hOr_U8FGC9s3BCGh98gQ6aBo8hM2igv5WhEdeYdG14e-6NMef73IGCLajt29RfoqmK0cbqnPVJoEVCuFROA9CNQDLCWEsDnqDnR9QU8peHMn5xCb1F9oH4r3_sWQ0gX0XIq_D6OnxDy1XTmYi7_XZfw2XawnizjOqm1w2GFE166x6T0tISakU4Cti5gVq9VGgSHRwwCnaVAa8uOw1kBVxpjYPqmcLW4h2w1S1xtGc7KO8iHvPDhYHVWDYdBbLbbhQWqWpk5P9ZSJSbhyXc2Kq1CgoxaVRGE_0y-rHARjuRU5KT7OQmqUtvK2YJkgzr2BR0kxlFvzRitZjhGgGCX6tdPSnXNtELzQjxupr7glABwOoX8zlv92u8DN8_Ebmw=w592-h154-no?authuser=0)
The two commanded body rates are calculate using some elements of the rotation matrix with a proportional error term in our rotation matrix.

Lastly, if the thrust is negative, then set these commanded body rates to zero.
# Altitude Controller
The altitude controller is implemented in ***lines 189-201***. The goal is to calculate the desired thrust we need to maintain the altitude with position, velocity, and acceleration inputs. The altitude is controlled through a simple PID loop where we take error terms in position and velocity and multiply them with the P and D gains. For the integrator term, the error term was multiplied by **dt** for each instance to get a sum of the area below the curve. 

After that, acceleration was calculated through the sum of these PID terms and constrained by specified descent and ascent rates. After acceleration, we can easily find thrust by multiplying with mass.
# Lateral Controller
The lateral controller is implemented in ***lines 239-243***. The goal is to calculate the desired horizontal acceleration with inputs from lateral position, velocity and acceleration.

The commanded acceleration is determined by a PD controller where we simply take errors in position and velocity and multiply them by their respective gains. We also add an acceleration feedforward term.
# Yaw Controller
The yaw controller is implemented in ***lines 265-277***. The goal is to calculate desired yaw rate with inputs - commanded yaw and the actual yaw.

There are two angles associated with the error between the commanded yaw and the actual yaw. One where you take the difference (commanded - actual) and one where you take that difference and add or subtract 2pi to it. One of these is smaller than the other.

The code in this portion is mostly checking for this very condition: which of these two angle options is smaller than the other? We can use fmodf on the commanded yaw so that we can reduce it to less than 2 pi (in case it was more than 2 pi), and start calculating the error and adding/subtracting 2 pi when needed.
# Generating Motor Commands
The code to implement the motor commands is found in ***lines 73-83***. The associated math to find these thrusts can be derived from these equations and with knowledge that the total thrust F is the sum of F1, F2, F3, and F4.
![enter image description here](https://lh3.googleusercontent.com/dgtrdxrxzQx9-UNyDCK4ulLACqEnM9I38fj58laP8G4j5hj1Y-R8rZ3PwjYxL4mAKzWer8cxEMQ9JQdbkNbHa-AzMwAnX741Nonix8yBvrI3P9FTcGeGXtQvJbw01PvSft6_6CoiHsQ8SskO45XabVgsUPilOVFwtq7ydJSc2O-LP9SyZKqGfgpdqVPWqF9D5ACl8TOUvNip8Dvl6lBMzMPyNwrn5L4PXRBbD4gAKPSvT2SVOLoF51xQe9LHbIA1uAGRIFgvANV7M0sFCtQtW320k6cb6aH3fJFnDyxcRa3auu15pvU4brgWfiSrEwVbcvDQJNCjE-QOhwMJUf60IIARwkvEq-fdGW90HvLApx-K3jtzCWYypMrFZsuB154JOq6lcvUWzBtcTBd_gdaz4QNikWvTpMWY_hy1i6oocARPyOpWLPr-NFbq5ZEHW3vv09Byd-kWnGTlEkGz-aCyrE87VUqSuArzMlTOlIbqPKec4kR8zUW6m8fk-5ttQOjhh2K_Ormg1vR7me3MM_DnKKykuc_yGT1VD4XL1-utwhVqk3HEB-dHTNEqR5iJwOvpdf-irS2mi6c2QrvS7r5x3Qxvu6ycbvJIQxX9U_Zt6-c95WDK1exgB8yAFL31wWKXKTDUs8ggkD1jonUtMyk1xnZ7aC9Jj3wA7MuVRBu2SowpoDPMG_5ObaasxvUUzuZi8Ii3NhNuh_snjeaEjqRb-0E=w988-h388-no?authuser=0)
Eventually, after solving for these four equations and four unknowns, you can solve for each force (F1,F2...) as a function of total thrust and the torques.



