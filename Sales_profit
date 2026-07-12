import React, { useState, useMemo } from 'react';
import { BarChart, Bar, LineChart, Line, PieChart, Pie, Cell, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer } from 'recharts';
import { TrendingUp, TrendingDown, DollarSign, ShoppingCart, Users, Globe } from 'lucide-react';

// Sample Data - Replace with your actual sales data
const salesData = [
  { month: 'Jan', sales: 8500000, profit: 1200000 },
  { month: 'Feb', sales: 9200000, profit: 1350000 },
  { month: 'Mar', sales: 10100000, profit: 1500000 },
  { month: 'Apr', sales: 7800000, profit: 1000000 },
  { month: 'May', sales: 8900000, profit: 1250000 },
  { month: 'Jun', sales: 11200000, profit: 1700000 },
  { month: 'Jul', sales: 10500000, profit: 1550000 },
  { month: 'Aug', sales: 11800000, profit: 1800000 },
  { month: 'Sep', sales: 10900000, profit: 1650000 },
  { month: 'Oct', sales: 13500000, profit: 2100000 },
  { month: 'Nov', sales: 14200000, profit: 2250000 },
  { month: 'Dec', sales: 12800000, profit: 1950000 }
];

const segmentData = [
  { name: 'Government', value: 44.22, color: '#3b82f6' },
  { name: 'Corporate', value: 32.15, color: '#10b981' },
  { name: 'Consumer', value: 23.63, color: '#f59e0b' }
];

const productData = [
  { name: 'Technology', sales: 45000000 },
  { name: 'Furniture', sales: 38000000 },
  { name: 'Office Supplies', sales: 36000000 }
];

const countryData = [
  { name: 'USA', sales: 35000000 },
  { name: 'Canada', sales: 28000000 },
  { name: 'UK', sales: 22000000 },
  { name: 'Germany', sales: 18000000 },
  { name: 'Others', sales: 16000000 }
];

export default function SalesDashboard() {
  const [selectedYear, setSelectedYear] = useState('2024');
  
  const totalSales = useMemo(() => salesData.reduce((acc, curr) => acc + curr.sales, 0), []);
  const totalProfit = useMemo(() => salesData.reduce((acc, curr) => acc + curr.profit, 0), []);
  const profitMargin = ((totalProfit / totalSales) * 100).toFixed(2);

  const KPICard = ({ title, value, change, icon: Icon, trend }) => (
    <div className="bg-white rounded-xl shadow-lg p-6 border border-gray-100 hover:shadow-xl transition-shadow">
      <div className="flex items-center justify-between">
        <div>
          <p className="text-sm font-medium text-gray-600">{title}</p>
          <p className="text-3xl font-bold text-gray-900 mt-2">{value}</p>
          <div className={`flex items-center mt-2 text-sm ${trend === 'up' ? 'text-green-600' : 'text-red-600'}`}>
            {trend === 'up' ? <TrendingUp className="w-4 h-4 mr-1" /> : <TrendingDown className="w-4 h-4 mr-1" />}
            <span>{change}</span>
          </div>
        </div>
        <div className="bg-blue-50 p-3 rounded-lg">
          <Icon className="w-8 h-8 text-blue-600" />
        </div>
      </div>
    </div>
  );

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-50 to-gray-100 p-6">
      <div className="max-w-7xl mx-auto">
        {/* Header */}
        <div className="mb-8">
          <h1 className="text-4xl font-bold text-gray-900 mb-2">Global Sales & Profit Analysis</h1>
          <p className="text-gray-600">Real-time insights into $119M+ sales performance</p>
        </div>

        {/* KPI Cards */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
          <KPICard title="Total Sales" value="$119.2M" change="+12.5%" icon={DollarSign} trend="up" />
          <KPICard title="Total Profit" value="$17.0M" change="+8.3%" icon={TrendingUp} trend="up" />
          <KPICard title="Profit Margin" value={`${profitMargin}%`} change="+1.2%" icon={ShoppingCart} trend="up" />
          <KPICard title="Active Markets" value="42" change="+3" icon={Globe} trend="up" />
        </div>

        {/* Charts Grid */}
        <div className="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-6">
          {/* Monthly Sales Trend */}
          <div className="bg-white rounded-xl shadow-lg p-6">
            <h3 className="text-lg font-semibold text-gray-900 mb-4">Monthly Sales Trend</h3>
            <ResponsiveContainer width="100%" height={300}>
              <LineChart data={salesData}>
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis dataKey="month" />
                <YAxis />
                <Tooltip formatter={(value) => `$${(value/1000000).toFixed(1)}M`} />
                <Legend />
                <Line type="monotone" dataKey="sales" stroke="#3b82f6" strokeWidth={3} name="Sales" />
                <Line type="monotone" dataKey="profit" stroke="#10b981" strokeWidth={3} name="Profit" />
              </LineChart>
            </ResponsiveContainer>
          </div>

          {/* Segment Distribution */}
          <div className="bg-white rounded-xl shadow-lg p-6">
            <h3 className="text-lg font-semibold text-gray-900 mb-4">Sales by Segment</h3>
            <ResponsiveContainer width="100%" height={300}>
              <PieChart>
                <Pie data={segmentData} cx="50%" cy="50%" labelLine={false} label={({name, value}) => `${name}: ${value}%`} outerRadius={80} fill="#8884d8" dataKey="value">
                  {segmentData.map((entry, index) => <Cell key={`cell-${index}`} fill={entry.color} />)}
                </Pie>
                <Tooltip />
              </PieChart>
            </ResponsiveContainer>
          </div>
        </div>

        {/* Product & Country Charts */}
        <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
          <div className="bg-white rounded-xl shadow-lg p-6">
            <h3 className="text-lg font-semibold text-gray-900 mb-4">Sales by Product</h3>
            <ResponsiveContainer width="100%" height={300}>
              <BarChart data={productData}>
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis dataKey="name" />
                <YAxis />
                <Tooltip formatter={(value) => `$${(value/1000000).toFixed(1)}M`} />
                <Bar dataKey="sales" fill="#3b82f6" radius={[8, 8, 0, 0]} />
              </BarChart>
            </ResponsiveContainer>
          </div>

          <div className="bg-white rounded-xl shadow-lg p-6">
            <h3 className="text-lg font-semibold text-gray-900 mb-4">Top Countries</h3>
            <ResponsiveContainer width="100%" height={300}>
              <BarChart data={countryData} layout="vertical">
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis type="number" />
                <YAxis dataKey="name" type="category" />
                <Tooltip formatter={(value) => `$${(value/1000000).toFixed(1)}M`} />
                <Bar dataKey="sales" fill="#10b981" radius={[0, 8, 8, 0]} />
              </BarChart>
            </ResponsiveContainer>
          </div>
        </div>
      </div>
    </div>
  );
}
