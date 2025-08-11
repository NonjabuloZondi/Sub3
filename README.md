#include <iostream>
#include <string>
using namespace std;

string orders[50] = {
    "101", "102", "103", "104", "105", "106", "107", "108", "109", "110",
    "0", "0", "0", "0", "0", "0", "0", "0", "0", "0",
    "0", "0", "0", "0", "0", "0", "0", "0", "0", "0",
    "0", "0", "0", "0", "0", "0", "0", "0", "0", "0",
    "0", "0", "0", "0", "0", "0", "0", "0", "0", "0"
};
string cnames[50] = {"Thabo","Lerato","Nomvula","Sipho","Bongani","Lindiwe","Jabulani","Ayanda","Kgosi","Refilwe"};
int noofmag[50] = {3,5,2,4,6,1,3,2,6,4};
float torders[50] = {15.75,30.50,10.00,22.00,40.25,5.50,18.00,12.75,28.00,24.50};
int len = 10;

int main() {
    int option = 0;
    while (true) {
        cout << "\n=== Order Management ===" << endl;
        cout << "1. Add a new order" << endl;
        cout << "2. Display all orders" << endl;
        cout << "3. Find an order by order ID" << endl;
        cout << "4. Calculate total revenue" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice (1-5): ";
        cin >> option;

        if (option == 1) {
            if (len < 50) {
                int idnumber = stoi(orders[len - 1]) + 1;
                orders[len] = to_string(idnumber);
                cout << "Enter Customer Name: ";
                cin >> cnames[len];
                cout << "Enter Number of Magwinyas Ordered: ";
                cin >> noofmag[len];
                cout << "Enter Total Amount: ";
                cin >> torders[len];
                cout << "✅ Entry successful! Order ID: " << idnumber << endl;
                len++;
            } else {
                cout << "❌ No more space in array." << endl;
            }
        }
        else if (option == 2) {
            cout << "\n📦 All Orders:" << endl;
            for (int i = 0; i < len; i++) {
                if (orders[i] != "0") {
                    cout << "-------------------------" << endl;
                    cout << "ID: " << orders[i] << endl;
                    cout << "Customer Name: " << cnames[i] << endl;
                    cout << "No. of Magwinyas: " << noofmag[i] << endl;
                    cout << "Total: R" << torders[i] << endl;
                }
            }
        }
        else if (option == 3) {
            string searchID;
            cout << "🔍 Enter Order ID to search: ";
            cin >> searchID;
            bool found = false;
            for (int i = 0; i < len; i++) {
                if (orders[i] == searchID) {
                    cout << "\n✅ Order Found:" << endl;
                    cout << "Customer Name: " << cnames[i] << endl;
                    cout << "No. of Magwinyas: " << noofmag[i] << endl;
                    cout << "Total: R" << torders[i] << endl;
                    found = true;
                    break;
                }
            }
            if (!found) {
                cout << "❌ Order ID not found." << endl;
            }
        }
        else if (option == 4) {
            float totalRevenue = 0;
            for (int i = 0; i < len; i++) {
                totalRevenue += torders[i];
            }
            cout << "\n💰 Total Revenue: R" << totalRevenue << endl;
        }
        else if (option == 5) {
            cout << "👋 Program closed. Goodbye!" << endl;
            break;
        }
        else {
            cout << "⚠️ Invalid Option. Please choose between 1 and 5." << endl;
        }
    }

    return 0;
}
