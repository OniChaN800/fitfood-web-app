import React from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";
import { BarChart, Bar, XAxis, YAxis, Tooltip, ResponsiveContainer, LineChart, Line } from "recharts";

const stepsData = [
  { name: "الاثنين", steps: 5600 },
  { name: "الثلاثاء", steps: 7200 },
  { name: "الأربعاء", steps: 4300 },
  { name: "الخميس", steps: 6900 },
  { name: "الجمعة", steps: 8000 },
  { name: "السبت", steps: 9200 },
  { name: "الأحد", steps: 6100 },
];

const weightData = [
  { date: "01-04", weight: 80 },
  { date: "05-04", weight: 79.5 },
  { date: "10-04", weight: 78.8 },
  { date: "15-04", weight: 78.2 },
];

export default function FitFoodApp() {
  return (
    <main className="min-h-screen bg-gray-100 p-4 font-sans">
      <h1 className="text-3xl font-bold text-center text-green-600 mb-6">منصة فيت فود</h1>

      <Tabs defaultValue="dashboard" className="w-full max-w-5xl mx-auto">
        <TabsList className="grid grid-cols-6 gap-2">
          <TabsTrigger value="dashboard">الملخص</TabsTrigger>
          <TabsTrigger value="meals">الوجبات</TabsTrigger>
          <TabsTrigger value="workouts">التمارين</TabsTrigger>
          <TabsTrigger value="profile">الملف الشخصي</TabsTrigger>
          <TabsTrigger value="consulting">الاستشارات</TabsTrigger>
          <TabsTrigger value="rewards">المكافآت</TabsTrigger>
        </TabsList>

        <TabsContent value="dashboard">
          <Card>
            <CardContent className="p-4 space-y-6">
              <div>
                <h2 className="text-xl font-semibold mb-2">النشاط الأسبوعي</h2>
                <ResponsiveContainer width="100%" height={250}>
                  <BarChart data={stepsData}>
                    <XAxis dataKey="name" />
                    <YAxis />
                    <Tooltip />
                    <Bar dataKey="steps" fill="#4CAF50" />
                  </BarChart>
                </ResponsiveContainer>
              </div>
              <div>
                <h2 className="text-xl font-semibold mb-2">تتبع الوزن</h2>
                <ResponsiveContainer width="100%" height={200}>
                  <LineChart data={weightData}>
                    <XAxis dataKey="date" />
                    <YAxis />
                    <Tooltip />
                    <Line type="monotone" dataKey="weight" stroke="#FF9800" strokeWidth={2} />
                  </LineChart>
                </ResponsiveContainer>
              </div>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="meals">
          <Card>
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-4">خطة الوجبات اليومية</h2>
              <ul className="space-y-2">
                <li>🥣 فطور: شوفان + موز + لوز</li>
                <li>🥗 غداء: صدر دجاج مشوي + أرز بني + سلطة</li>
                <li>🍎 سناك: تفاحة + زبادي</li>
                <li>🥘 عشاء: شوربة عدس + خبز أسمر</li>
              </ul>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="workouts">
          <Card>
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-4">تمارين اليوم</h2>
              <ul className="space-y-2">
                <li>🏋️‍♂️ سكوات – 3 مجموعات × 15 تكرار</li>
                <li>💪 تمرين الضغط – 3 مجموعات × 12 تكرار</li>
                <li>🧘‍♀️ بلانك – 3 مرات × 45 ثانية</li>
              </ul>
              <Button className="mt-4">ابدأ التمرين</Button>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="profile">
          <Card>
            <CardContent className="p-4 space-y-4">
              <h2 className="text-xl font-semibold">الملف الشخصي</h2>
              <Input placeholder="الاسم الكامل" />
              <Input placeholder="البريد الإلكتروني" />
              <Input placeholder="الوزن الحالي (كجم)" />
              <Button>حفظ البيانات</Button>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="consulting">
          <Card>
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-4">استشارات المختصين</h2>
              <p className="mb-4">اختر الفئة العمرية والمجال الصحي الذي ترغب بالحصول على استشارة فيه.</p>
              <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                <Button>استشارة تغذية – الأطفال</Button>
                <Button>استشارة لياقة – البالغين</Button>
                <Button>استشارة صحية – كبار السن</Button>
                <Button>أخصائي نفسي – دعم نمط الحياة</Button>
              </div>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="rewards">
          <Card>
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-4">نظام المكافآت</h2>
              <p>تحصل على نقاط عند تحقيق أهدافك اليومية أو الأسبوعية.</p>
              <ul className="mt-4 space-y-2">
                <li>✅ 1000 خطوة = 1 نقطة</li>
                <li>✅ اتباع خطة وجبات يومية = 5 نقاط</li>
                <li>✅ إتمام تمرين يومي = 5 نقاط</li>
              </ul>
              <div className="mt-4 font-bold">رصيدك الحالي: <span className="text-green-600">35 نقطة</span></div>
              <Button className="mt-2">استبدل النقاط</Button>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>
    </main>
  );
}
