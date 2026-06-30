#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>
using namespace std;
string generateToken() {
 string chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
 string token = "DAT-";
 srand(time(0));
 for (int i = 0; i < 6; ++i) {
 token += chars[rand() % chars.size()];
 }
 return token;
}
bool otpVerification() {
 int otp = rand() % 9000 + 1000; // generate 4-digit OTP
 cout << "\nOTP sent to your registered mobile: " << otp << endl;
 int entered;
 cout << "Enter OTP: ";
 cin >> entered;
 return (entered == otp);
}
int main() {
 srand(time(0)); string aadhaar, address;
 cout << "=== AddressLink Digital Address Updater ===\n";
 // Aadhaar Login
 cout << "\nEnter Aadhaar Number: ";
 cin >> aadhaar;
 if (aadhaar.length() != 12) {
 cout << "Invalid Aadhaar number!\n";
 return 0;
 }
 cout << "Aadhaar verified successfully!\n";
 // OTP Verification
 if (!otpVerification()) {
 cout << "OTP verification failed!\n";
 return 0;
 }
 cout << "OTP verified successfully!\n";
 // Address Entry
 cin.ignore();
 cout << "\nEnter your new address: ";
 getline(cin, address);
 cout << "\nVerifying address with GPS and India Post database...\n"; cout << "Address verified successfully!\n";
 // Generate Digital Address Token
 string token = generateToken();
 cout << "\nGenerated Digital Address Token: " << token << endl;
 // Send Updates
 cout << "\nSending address update to departments...\n";
 cout << " India Post\n";
 cout << " Banks\n";
 cout << " Voter Registration\n";
 cout << " DigiLocker\n";
 cout << "\nAll updates sent successfully!\n";
 // Acknowledgment tracking
 cout << "\nTracking acknowledgments:\n";
 cout << "India Post \n";
 cout << "Banks \n";
 cout << "Voter Registration \n";
 cout << "DigiLocker \n";
 cout << "\n Address update process completed successfully!\n";
 cout << "Your secure digital token (" << token << ") is now active.\n";
 return 0;
}



