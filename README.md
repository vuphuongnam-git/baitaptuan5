# baitaptuan5
Bài 1:

#include<iostream>

using namespace std;

void nhapDay(int a[], int n) { // ham nhap mang

for (int i = 0; i < n; i++) {

cout << "Nhap phan tu thu " << i << " : ";

cin >> a[i];

}

}

void sapXep(int a[], int n) { // ham sap xep theo thu tu tang dan

int tg;

for (int i2 = 0; i2 < n - 1; i2++) {

for (int i3 = i2 + 1; i3 < n; i3++) {

if (a[i2] > a[i3]) {

tg = a[i2];

a[i2] = a[i3];

a[i3] = tg;

}

}

}

}

void inDay(int a[], int n) { // ham in mang

for (int i4 = 0; i4 < n; i4++) {

cout << " " << a[i4];

}

}

void checkTanSuat(int a[], int n) { // ham check tan suat va in

int dem;

int ts[2][10];

for (int i5 = 0; i5 < 10; i5++) {

ts[0][i5] = a[i5];

ts[1][i5] = 1;

}

dem = 1;

for (int i = 0; i < 9; i++) {

for (int j = i + 1; j < 10; j++) {

if (a[i] == a[j]) {

dem = dem + 1;

ts[1][i] = dem;

ts[0][j] = 0;

}

}

dem = 1;

}

int max = ts[1][0];

for (int i6 = 0; i6 < 10; i6++) {

if (ts[1][i6] > max)

max = ts[1][i6];

}

if (max > 1) {

cout << "\n So co tan suat xuat hien nhieu nhat la: ";

for (int i7 = 0; i7 < 10; i7++) {

if (ts[1][i7] == max) cout << " " << a[i7];

}

cout << " - voi " << max << " lan xuat hien.";

}

else

cout << " \nCac so deu xuat hien chi co 1 lan :)) ";

cout << "\n";

for (int i8 = 0; i8 < 10; i8++) {

if (ts[0][i8] != 0) {

cout << " So " << a[i8] << " xuat hien " << ts[1][i8] << " lan";

cout << " \n";

}

}

}

int main() {

int a[10], n = 10;

nhapDay(a, n);

sapXep(a, n);

cout << "\n Day sap xep theo thu tu tang dan la: ";

inDay(a, n);

checkTanSuat(a, n);

cout << "Gia tri max la : " << a[9] << "\n" << "Gia tri min cua day la: " << a[0] << endl;

return 0;

}

Bài 2:

#include <iostream>

using namespace std;

struct Node

{

float data;

Node* next;

};

// khai bao danh sach

struct List

{

Node* firstNode;

Node* finalNode;

};

// khoi tao danh sach

void List_Init(List* list)

{

list->firstNode = NULL;

list->finalNode = NULL;

}

//them phan tu vao dau danh sach

Node* List_Add(List* list, float data)

{

Node* newnode = new Node;

newnode->data = data;

newnode->next = list->firstNode;

list->firstNode = newnode;

return newnode;

}

int List_Length(List* list)

{

Node* node = list->firstNode;

int i = 0;

while (node != NULL) {

i++;

node = node->next;

}

return i;

}

//hien thi noi dung phan tu trong danh sach

void List_Display(List* list)

{

Node* node = list->firstNode;

int i = List_Length(list);

cout << "\nDo dai cua list:\t" << i;

if (list->firstNode == 0)

cout << "\nList rong\r\n";

else

{

while (node != NULL)

{

cout << "\ndia chi cua node " << i << "\t" << &node->data;

cout << "\nnode->data:\t\t" << node->data;

cout << "\nnode->next:\t\t" << node->next << "\n";

node = node->next;

i--;

}

}

}

Node* Themphantu(List* list, float data, int k)

{

Node* p = List_Add(list, data);

list->firstNode = p->next;

Node* q = list->firstNode;

Node* r = list->firstNode;

if (k == 1)

{

Node* p = List_Add(list, data);

return p;

}

int dem = 0;

while (r != NULL && dem != k - 1)

{

dem++;

if (dem < k - 1)

q = q->next;

r = r->next;

}

p->next = r;

q->next = p;

}

Node* XoaPhanTu(List* list, int k)

{

Node* p = list->firstNode;

Node* q = list->firstNode;

if (k == 1)

list->firstNode = list->firstNode->next;

int dem = 0;

while (dem != k && q != NULL)

{

dem++;

if (dem < k - 1)

p = p->next;

if (dem <= k)

q = q->next;

}

p->next = q;

}

int main()

{

List list1;

List_Init(&list1);

List_Display(&list1);

List_Add(&list1, 1);//list: 1

List_Add(&list1, 2);//list: 2 1

cout << "Noi dung list sau hai lenh List_Add:";

List_Display(&list1);

cout << "Noi dung list sau khi them 2 lenh List_Add nua:";

List_Add(&list1, 3);//list: 3 2 1

List_Add(&list1, 4);//list 4 3 2 1

List_Display(&list1);

cout << "Day sau khi them phan tu la:\n";

Themphantu(&list1, 8, 3);

List_Display(&list1);

cout << "Day sau khi xoa phan tu la:\n";

XoaPhanTu(&list1, 2);

List_Display(&list1);

return 0;

}
