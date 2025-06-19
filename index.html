import React, { useState, useEffect } from 'react';
import { Users, Calendar, Gift, CreditCard, Bell, CheckCircle, Clock, Star, Plus, Search, Edit, Trash2, Phone, Mail, MapPin, TrendingUp, Award, AlertCircle, Download } from 'lucide-react';

const MembershipManagementSystem = () => {
  const [activeTab, setActiveTab] = useState('activation');
  const [searchTerm, setSearchTerm] = useState('');
  const [selectedMember, setSelectedMember] = useState(null);
  const [showMemberDetails, setShowMemberDetails] = useState(false);
  
  const [members, setMembers] = useState([
    {
      id: 'M001',
      name: 'Sarah Chen',
      phone: '+60123456789',
      email: 'sarah@email.com',
      address: 'Shah Alam, Selangor',
      joinDate: '2024-01-15',
      expiryDate: '2025-01-15',
      duration: '12 months',
      status: 'Active',
      points: 450,
      visits: 12,
      totalSpent: 480.50,
      lastVisit: '2024-06-10',
      favoriteItems: ['Special Fried Rice', 'Seafood Fried Rice']
    },
    {
      id: 'M002',
      name: 'Ahmad Rahman',
      phone: '+60198765432',
      email: 'ahmad@email.com',
      address: 'Petaling Jaya, Selangor',
      joinDate: '2024-02-20',
      expiryDate: '2025-02-20',
      duration: '12 months',
      status: 'Expiring Soon',
      points: 280,
      visits: 8,
      totalSpent: 320.00,
      lastVisit: '2024-06-05',
      favoriteItems: ['Chicken Fried Rice']
    },
    {
      id: 'M003',
      name: 'Priya Sharma',
      phone: '+60167890123',
      email: 'priya@email.com',
      address: 'Subang Jaya, Selangor',
      joinDate: '2024-03-10',
      expiryDate: '2025-09-10',
      duration: '18 months',
      status: 'Active',
      points: 150,
      visits: 5,
      totalSpent: 180.00,
      lastVisit: '2024-06-12',
      favoriteItems: ['Vegetable Fried Rice', 'Tom Yam Fried Rice']
    }
  ]);

  const [newMember, setNewMember] = useState({
    name: '',
    phone: '',
    email: '',
    address: '',
    duration: '12'
  });



  const addNewMember = () => {
    if (newMember.name && newMember.phone) {
      const memberId = `M${String(members.length + 1).padStart(3, '0')}`;
      const today = new Date();
      const expiry = new Date(today);
      expiry.setMonth(expiry.getMonth() + parseInt(newMember.duration));

      const member = {
        id: memberId,
        name: newMember.name,
        phone: newMember.phone,
        email: newMember.email,
        address: newMember.address,
        joinDate: today.toISOString().split('T')[0],
        expiryDate: expiry.toISOString().split('T')[0],
        duration: `${newMember.duration} months`,
        status: 'Active',
        points: 0,
        visits: 0,
        totalSpent: 0,
        lastVisit: null,
        favoriteItems: []
      };

      setMembers([...members, member]);
      setNewMember({ name: '', phone: '', email: '', address: '', duration: '12' });
    }
  };

  const updateMemberTier = (member) => {
    return 'Member'; // Simple membership without tiers
  };

  const getStatusColor = (status) => {
    switch(status) {
      case 'Active': return 'bg-green-100 text-green-800';
      case 'Expiring Soon': return 'bg-yellow-100 text-yellow-800';
      case 'Expired': return 'bg-red-100 text-red-800';
      case 'Inactive': return 'bg-gray-100 text-gray-800';
      default: return 'bg-gray-100 text-gray-800';
    }
  };

  const getDaysToExpiry = (expiryDate) => {
    const today = new Date();
    const expiry = new Date(expiryDate);
    const diffTime = expiry - today;
    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    return diffDays;
  };

  const expiringMembers = members.filter(member => {
    const daysToExpiry = getDaysToExpiry(member.expiryDate);
    return daysToExpiry <= 30 && daysToExpiry > 0;
  });

  const filteredMembers = members.filter(member =>
    member.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
    member.phone.includes(searchTerm) ||
    member.id.toLowerCase().includes(searchTerm.toLowerCase())
  );

  const renewMembership = (memberId, duration = 12) => {
    setMembers(members.map(member => {
      if (member.id === memberId) {
        const newExpiry = new Date();
        newExpiry.setMonth(newExpiry.getMonth() + duration);
        return {
          ...member,
          expiryDate: newExpiry.toISOString().split('T')[0],
          status: 'Active'
        };
      }
      return member;
    }));
  };

  const totalMembers = members.length;
  const activeMembers = members.filter(m => m.status === 'Active').length;
  const totalRevenue = members.reduce((sum, m) => sum + m.totalSpent, 0);
  const averageSpent = totalRevenue / totalMembers;

  return (
    <div className="max-w-7xl mx-auto p-6 bg-gray-50 min-h-screen">
      {/* Header */}
      <div className="bg-gradient-to-r from-orange-500 to-red-500 rounded-xl shadow-lg p-8 mb-6 text-white">
        <h1 className="text-3xl font-bold mb-2">🍚 Fried Rice Shop - Membership Management</h1>
        <p className="text-orange-100">Activate, track, and manage your customer memberships</p>
        
        {/* Quick Stats */}
        <div className="grid grid-cols-2 md:grid-cols-4 gap-4 mt-6">
          <div className="bg-white bg-opacity-20 rounded-lg p-4">
            <div className="text-2xl font-bold">{totalMembers}</div>
            <div className="text-sm text-orange-100">Total Members</div>
          </div>
          <div className="bg-white bg-opacity-20 rounded-lg p-4">
            <div className="text-2xl font-bold">{activeMembers}</div>
            <div className="text-sm text-orange-100">Active Members</div>
          </div>
          <div className="bg-white bg-opacity-20 rounded-lg p-4">
            <div className="text-2xl font-bold">RM{totalRevenue.toFixed(0)}</div>
            <div className="text-sm text-orange-100">Total Revenue</div>
          </div>
          <div className="bg-white bg-opacity-20 rounded-lg p-4">
            <div className="text-2xl font-bold">{expiringMembers.length}</div>
            <div className="text-sm text-orange-100">Expiring Soon</div>
          </div>
        </div>
      </div>

      {/* Tab Navigation */}
      <div className="bg-white rounded-lg shadow-md mb-6">
        <div className="flex border-b overflow-x-auto">
          <button
            onClick={() => setActiveTab('activation')}
            className={`px-6 py-3 font-medium whitespace-nowrap ${activeTab === 'activation' 
              ? 'border-b-2 border-orange-500 text-orange-600' 
              : 'text-gray-500 hover:text-gray-700'}`}
          >
            <Users className="w-4 h-4 inline mr-2" />
            Member Activation
          </button>
          <button
            onClick={() => setActiveTab('tracking')}
            className={`px-6 py-3 font-medium whitespace-nowrap ${activeTab === 'tracking' 
              ? 'border-b-2 border-orange-500 text-orange-600' 
              : 'text-gray-500 hover:text-gray-700'}`}
          >
            <Calendar className="w-4 h-4 inline mr-2" />
            Membership Tracking
          </button>
          <button
            onClick={() => setActiveTab('renewals')}
            className={`px-6 py-3 font-medium whitespace-nowrap ${activeTab === 'renewals' 
              ? 'border-b-2 border-orange-500 text-orange-600' 
              : 'text-gray-500 hover:text-gray-700'}`}
          >
            <Bell className="w-4 h-4 inline mr-2" />
            Renewal Alerts ({expiringMembers.length})
          </button>
          <button
            onClick={() => setActiveTab('analytics')}
            className={`px-6 py-3 font-medium whitespace-nowrap ${activeTab === 'analytics' 
              ? 'border-b-2 border-orange-500 text-orange-600' 
              : 'text-gray-500 hover:text-gray-700'}`}
          >
            <TrendingUp className="w-4 h-4 inline mr-2" />
            Analytics
          </button>
        </div>

        {/* Member Activation Tab */}
        {activeTab === 'activation' && (
          <div className="p-6">
            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
              {/* Activation Form */}
              <div className="space-y-6">
                <h2 className="text-xl font-bold text-gray-800">New Member Registration</h2>
                
                <div className="space-y-4">
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">Full Name *</label>
                    <input
                      type="text"
                      value={newMember.name}
                      onChange={(e) => setNewMember({...newMember, name: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-transparent"
                      placeholder="Enter customer name"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">Phone Number *</label>
                    <input
                      type="text"
                      value={newMember.phone}
                      onChange={(e) => setNewMember({...newMember, phone: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-transparent"
                      placeholder="+60xxxxxxxxx"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">Email (Optional)</label>
                    <input
                      type="email"
                      value={newMember.email}
                      onChange={(e) => setNewMember({...newMember, email: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-transparent"
                      placeholder="customer@email.com"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">Address (Optional)</label>
                    <input
                      type="text"
                      value={newMember.address}
                      onChange={(e) => setNewMember({...newMember, address: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-transparent"
                      placeholder="City, State"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">Membership Duration</label>
                    <select
                      value={newMember.duration}
                      onChange={(e) => setNewMember({...newMember, duration: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-transparent"
                    >
                      <option value="1">1 Month</option>
                      <option value="3">3 Months</option>
                      <option value="6">6 Months</option>
                      <option value="12">12 Months (Most Popular)</option>
                      <option value="18">18 Months</option>
                      <option value="24">24 Months</option>
                    </select>
                  </div>

                  <button
                    onClick={addNewMember}
                    disabled={!newMember.name || !newMember.phone}
                    className="w-full bg-orange-500 hover:bg-orange-600 disabled:bg-gray-300 disabled:cursor-not-allowed text-white py-3 px-4 rounded-lg font-medium transition-colors flex items-center justify-center"
                  >
                    <Plus className="w-4 h-4 mr-2" />
                    Activate Membership
                  </button>
                </div>
              </div>

              {/* Basic Membership Info */}
              <div className="space-y-4">
                <h2 className="text-xl font-bold text-gray-800">Membership Information</h2>
                
                <div className="border rounded-lg p-6 bg-orange-50">
                  <div className="flex items-center mb-4">
                    <Award className="w-6 h-6 text-orange-500 mr-3" />
                    <h3 className="font-semibold text-gray-800 text-lg">Fried Rice Club Member</h3>
                  </div>
                  <p className="text-gray-700">
                    Join our membership program to enjoy exclusive benefits and track your dining history with us.
                  </p>
                </div>

                <div className="bg-blue-50 border border-blue-200 rounded-lg p-4">
                  <h4 className="font-medium text-blue-800 mb-2">💡 Duration Recommendations:</h4>
                  <ul className="text-sm text-blue-700 space-y-1">
                    <li><strong>12 months:</strong> Most popular, best value</li>
                    <li><strong>6 months:</strong> Good for trying membership</li>
                    <li><strong>24 months:</strong> Longest commitment, great for regulars</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        )}

        {/* Membership Tracking Tab */}
        {activeTab === 'tracking' && (
          <div className="p-6">
            <div className="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-6 gap-4">
              <h2 className="text-xl font-bold text-gray-800">All Members ({filteredMembers.length})</h2>
              <div className="flex items-center space-x-4">
                <div className="relative">
                  <Search className="w-4 h-4 absolute left-3 top-3 text-gray-400" />
                  <input
                    type="text"
                    placeholder="Search members..."
                    value={searchTerm}
                    onChange={(e) => setSearchTerm(e.target.value)}
                    className="pl-10 pr-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500 focus:border-transparent"
                  />
                </div>
                <button className="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-sm font-medium transition-colors flex items-center">
                  <Download className="w-4 h-4 mr-2" />
                  Export
                </button>
              </div>
            </div>

            <div className="overflow-x-auto">
              <table className="w-full border-collapse bg-white rounded-lg shadow">
                <thead className="bg-gray-50">
                  <tr>
                    <th className="p-4 text-left font-medium text-gray-700">Member</th>
                    <th className="p-4 text-left font-medium text-gray-700">Contact</th>
                    <th className="p-4 text-left font-medium text-gray-700">Status</th>
                    <th className="p-4 text-left font-medium text-gray-700">Stats</th>
                    <th className="p-4 text-left font-medium text-gray-700">Expiry</th>
                    <th className="p-4 text-left font-medium text-gray-700">Actions</th>
                  </tr>
                </thead>
                <tbody>
                  {filteredMembers.map((member) => {
                    const daysToExpiry = getDaysToExpiry(member.expiryDate);
                    const currentTier = updateMemberTier(member);
                    return (
                      <tr key={member.id} className="border-t hover:bg-gray-50">
                        <td className="p-4">
                          <div>
                            <div className="font-medium text-gray-800">{member.name}</div>
                            <div className="text-sm text-gray-500 font-mono">{member.id}</div>
                          </div>
                        </td>
                        <td className="p-4">
                          <div className="space-y-1">
                            <div className="flex items-center text-sm text-gray-600">
                              <Phone className="w-3 h-3 mr-1" />
                              {member.phone}
                            </div>
                            {member.email && (
                              <div className="flex items-center text-sm text-gray-600">
                                <Mail className="w-3 h-3 mr-1" />
                                {member.email}
                              </div>
                            )}
                            {member.address && (
                              <div className="flex items-center text-sm text-gray-600">
                                <MapPin className="w-3 h-3 mr-1" />
                                {member.address}
                              </div>
                            )}
                          </div>
                        </td>
                        <td className="p-4">
                          <span className={`px-2 py-1 rounded-full text-xs font-medium ${getStatusColor(member.status)}`}>
                            {member.status}
                          </span>
                        </td>
                        <td className="p-4">
                          <div className="space-y-1 text-sm">
                            <div className="flex items-center">
                              <Star className="w-3 h-3 text-yellow-500 mr-1" />
                              {member.points} pts
                            </div>
                            <div>{member.visits} visits</div>
                            <div className="font-medium">RM{member.totalSpent.toFixed(2)}</div>
                          </div>
                        </td>
                        <td className="p-4">
                          <div className="text-sm">
                            <div className={daysToExpiry <= 30 ? 'text-orange-600 font-medium' : ''}>
                              {member.expiryDate}
                            </div>
                            <div className={`text-xs ${daysToExpiry <= 30 ? 'text-orange-500' : 'text-gray-500'}`}>
                              {daysToExpiry > 0 ? `${daysToExpiry} days left` : 'Expired'}
                            </div>
                          </div>
                        </td>
                        <td className="p-4">
                          <div className="flex space-x-2">
                            <button
                              onClick={() => {
                                setSelectedMember(member);
                                setShowMemberDetails(true);
                              }}
                              className="text-blue-600 hover:text-blue-800 p-1"
                              title="View Details"
                            >
                              <Edit className="w-4 h-4" />
                            </button>
                          </div>
                        </td>
                      </tr>
                    );
                  })}
                </tbody>
              </table>
            </div>
          </div>
        )}

        {/* Renewal Alerts Tab */}
        {activeTab === 'renewals' && (
          <div className="p-6">
            <div className="flex justify-between items-center mb-6">
              <h2 className="text-xl font-bold text-gray-800">Membership Renewal Alerts</h2>
              {expiringMembers.length > 0 && (
                <button className="bg-orange-500 hover:bg-orange-600 text-white px-4 py-2 rounded-lg text-sm font-medium transition-colors">
                  Send All Reminders
                </button>
              )}
            </div>
            
            {expiringMembers.length === 0 ? (
              <div className="text-center py-12">
                <CheckCircle className="w-16 h-16 text-green-500 mx-auto mb-4" />
                <h3 className="text-lg font-medium text-gray-800 mb-2">All Good!</h3>
                <p className="text-gray-600">No memberships expiring in the next 30 days.</p>
              </div>
            ) : (
              <div className="space-y-4">
                <div className="bg-yellow-50 border border-yellow-200 rounded-lg p-4 mb-4">
                  <div className="flex items-center">
                    <AlertCircle className="w-5 h-5 text-yellow-600 mr-2" />
                    <span className="font-medium text-yellow-800">
                      {expiringMembers.length} membership{expiringMembers.length > 1 ? 's' : ''} expiring soon
                    </span>
                  </div>
                </div>

                {expiringMembers.map((member) => {
                  const daysToExpiry = getDaysToExpiry(member.expiryDate);
                  return (
                    <div key={member.id} className="bg-white border border-yellow-200 rounded-lg p-6 shadow-sm">
                      <div className="flex items-center justify-between mb-4">
                        <div className="flex items-center space-x-4">
                          <div className="flex-shrink-0">
                            <div className={`w-10 h-10 rounded-full flex items-center justify-center ${
                              daysToExpiry <= 7 ? 'bg-red-100' : 'bg-yellow-100'
                            }`}>
                              <Clock className={`w-5 h-5 ${
                                daysToExpiry <= 7 ? 'text-red-600' : 'text-yellow-600'
                              }`} />
                            </div>
                          </div>
                          <div>
                            <h3 className="font-semibold text-gray-800 text-lg">{member.name}</h3>
                            <div className="flex items-center space-x-4 text-sm text-gray-600 mt-1">
                              <span>{member.phone}</span>
                              <span>•</span>
                              <span>{member.duration}</span>
                            </div>
                          </div>
                        </div>
                        <div className="text-right">
                          <div className={`text-lg font-bold ${
                            daysToExpiry <= 7 ? 'text-red-600' : 'text-yellow-600'
                          }`}>
                            {daysToExpiry} days
                          </div>
                          <div className="text-xs text-gray-500">until expiry</div>
                        </div>
                      </div>
                      
                      <div className="bg-gray-50 rounded-lg p-4 mb-4">
                        <div className="grid grid-cols-3 gap-4 text-sm">
                          <div className="text-center">
                            <div className="font-semibold text-gray-800">{member.visits}</div>
                            <div className="text-gray-600">Total Visits</div>
                          </div>
                          <div className="text-center">
                            <div className="font-semibold text-gray-800">RM{member.totalSpent.toFixed(2)}</div>
                            <div className="text-gray-600">Total Spent</div>
                          </div>
                          <div className="text-center">
                            <div className="font-semibold text-gray-800">{member.points}</div>
                            <div className="text-gray-600">Points Balance</div>
                          </div>
                        </div>
                      </div>
                      
                      <div className="flex flex-wrap gap-2">
                        <button className="bg-yellow-500 hover:bg-yellow-600 text-white px-4 py-2 rounded-lg text-sm font-medium transition-colors flex items-center">
                          <Bell className="w-4 h-4 mr-2" />
                          Send Reminder
                        </button>
                        <button 
                          onClick={() => renewMembership(member.id, 12)}
                          className="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-sm font-medium transition-colors flex items-center"
                        >
                          <CheckCircle className="w-4 h-4 mr-2" />
                          Renew 12 Months
                        </button>
                        <button className="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-medium transition-colors flex items-center">
                          <Gift className="w-4 h-4 mr-2" />
                          Special Offer
                        </button>
                      </div>
                    </div>
                  );
                })}
              </div>
            )}
          </div>
        )}

        {/* Analytics Tab */}
        {activeTab === 'analytics' && (
          <div className="p-6">
            <h2 className="text-xl font-bold text-gray-800 mb-6">Membership Analytics</h2>
            
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
              {/* Key Metrics Cards */}
              <div className="bg-gradient-to-r from-blue-500 to-blue-600 text-white p-6 rounded-lg">
                <div className="flex items-center justify-between">
                  <div>
                    <p className="text-blue-100">Total Revenue</p>
                    <p className="text-2xl font-bold">RM{totalRevenue.toFixed(2)}</p>
                  </div>
                  <TrendingUp className="w-8 h-8 text-blue-200" />
                </div>
              </div>

              <div className="bg-gradient-to-r from-green-500 to-green-600 text-white p-6 rounded-lg">
                <div className="flex items-center justify-between">
                  <div>
                    <p className="text-green-100">Active Rate</p>
                    <p className="text-2xl font-bold">{((activeMembers/totalMembers)*100).toFixed(1)}%</p>
                  </div>
                  <Users className="w-8 h-8 text-green-200" />
                </div>
              </div>

              <div className="bg-gradient-to-r from-purple-500 to-purple-600 text-white p-6 rounded-lg">
                <div className="flex items-center justify-between">
                  <div>
                    <p className="text-purple-100">Avg. Spent</p>
                    <p className="text-2xl font-bold">RM{averageSpent.toFixed(2)}</p>
                  </div>
                  <CreditCard className="w-8 h-8 text-purple-200" />
                </div>
              </div>

              <div className="bg-gradient-to-r from-orange-500 to-orange-600 text-white p-6 rounded-lg">
                <div className="flex items-center justify-between">
                  <div>
                    <p className="text-orange-100">Retention Alert</p>
                    <p className="text-2xl font-bold">{expiringMembers.length}</p>
                  </div>
                  <Bell className="w-8 h-8 text-orange-200" />
                </div>
              </div>
            </div>

            {/* Charts and Analysis */}
            <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
              {/* Membership Status */}
              <div className="bg-white p-6 rounded-lg shadow">
                <h3 className="text-lg font-semibold text-gray-800 mb-4">Membership Status</h3>
                <div className="space-y-3">
                  {['Active', 'Expiring Soon', 'Expired', 'Inactive'].map(status => {
                    const statusMembers = members.filter(m => m.status === status).length;
                    const percentage = (statusMembers / totalMembers * 100).toFixed(1);
                    return (
                      <div key={status} className="flex items-center justify-between">
                        <div className="flex items-center">
                          <span className={`px-3 py-1 rounded-full text-xs font-medium ${getStatusColor(status)}`}>
                            {status}
                          </span>
                          <span className="ml-3 text-sm text-gray-600">{statusMembers} members</span>
                        </div>
                        <span className="text-sm font-semibold text-gray-800">{percentage}%</span>
                      </div>
                    );
                  })}
                </div>
              </div>

              {/* Top Spenders */}
              <div className="bg-white p-6 rounded-lg shadow">
                <h3 className="text-lg font-semibold text-gray-800 mb-4">Top Spenders</h3>
                <div className="space-y-3">
                  {members
                    .sort((a, b) => b.totalSpent - a.totalSpent)
                    .slice(0, 5)
                    .map((member, index) => (
                      <div key={member.id} className="flex items-center justify-between">
                        <div className="flex items-center">
                          <div className="w-8 h-8 bg-gradient-to-r from-yellow-400 to-yellow-500 rounded-full flex items-center justify-center text-white text-sm font-bold">
                            {index + 1}
                          </div>
                          <div className="ml-3">
                            <div className="font-medium text-gray-800">{member.name}</div>
                            <div className="text-xs text-gray-500">{member.visits} visits</div>
                          </div>
                        </div>
                        <div className="text-right">
                          <div className="font-semibold text-gray-800">RM{member.totalSpent.toFixed(2)}</div>
                          <div className="text-xs text-gray-500">{member.points} pts</div>
                        </div>
                      </div>
                    ))}
                </div>
              </div>

              {/* Recent Activity */}
              <div className="bg-white p-6 rounded-lg shadow">
                <h3 className="text-lg font-semibold text-gray-800 mb-4">Recent Activity</h3>
                <div className="space-y-3">
                  {members
                    .filter(m => m.lastVisit)
                    .sort((a, b) => new Date(b.lastVisit) - new Date(a.lastVisit))
                    .slice(0, 5)
                    .map(member => (
                      <div key={member.id} className="flex items-center justify-between">
                        <div className="flex items-center">
                          <div className="w-2 h-2 bg-green-500 rounded-full mr-3"></div>
                          <div>
                            <div className="font-medium text-gray-800">{member.name}</div>
                            <div className="text-xs text-gray-500">Last visit: {member.lastVisit}</div>
                          </div>
                        </div>
                        <span className="px-2 py-1 rounded-full text-xs font-medium bg-blue-100 text-blue-800">
                          Member
                        </span>
                      </div>
                    ))}
                </div>
              </div>
            </div>
          </div>
        )}
      </div>

      {/* Member Details Modal */}
      {showMemberDetails && selectedMember && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50">
          <div className="bg-white rounded-lg max-w-2xl w-full max-h-[90vh] overflow-y-auto">
            <div className="p-6 border-b">
              <div className="flex justify-between items-center">
                <h3 className="text-xl font-bold text-gray-800">Member Details</h3>
                <button
                  onClick={() => setShowMemberDetails(false)}
                  className="text-gray-500 hover:text-gray-700"
                >
                  ×
                </button>
              </div>
            </div>
            
            <div className="p-6">
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <h4 className="font-semibold text-gray-800 mb-3">Personal Information</h4>
                  <div className="space-y-2 text-sm">
                    <div><strong>ID:</strong> {selectedMember.id}</div>
                    <div><strong>Name:</strong> {selectedMember.name}</div>
                    <div><strong>Phone:</strong> {selectedMember.phone}</div>
                    <div><strong>Email:</strong> {selectedMember.email || 'Not provided'}</div>
                    <div><strong>Address:</strong> {selectedMember.address || 'Not provided'}</div>
                  </div>
                </div>
                
                <div>
                  <h4 className="font-semibold text-gray-800 mb-3">Membership Details</h4>
                  <div className="space-y-2 text-sm">
                    <div><strong>Join Date:</strong> {selectedMember.joinDate}</div>
                    <div><strong>Expiry Date:</strong> {selectedMember.expiryDate}</div>
                    <div><strong>Duration:</strong> {selectedMember.duration}</div>
                    <div><strong>Status:</strong> 
                      <span className={`ml-2 px-2 py-1 rounded-full text-xs font-medium ${getStatusColor(selectedMember.status)}`}>
                        {selectedMember.status}
                      </span>
                    </div>
                  </div>
                </div>
              </div>
              
              <div className="mt-6">
                <h4 className="font-semibold text-gray-800 mb-3">Activity Summary</h4>
                <div className="grid grid-cols-4 gap-4 text-center">
                  <div className="bg-blue-50 p-3 rounded-lg">
                    <div className="font-bold text-blue-600">{selectedMember.points}</div>
                    <div className="text-xs text-blue-600">Points</div>
                  </div>
                  <div className="bg-green-50 p-3 rounded-lg">
                    <div className="font-bold text-green-600">{selectedMember.visits}</div>
                    <div className="text-xs text-green-600">Visits</div>
                  </div>
                  <div className="bg-purple-50 p-3 rounded-lg">
                    <div className="font-bold text-purple-600">RM{selectedMember.totalSpent.toFixed(2)}</div>
                    <div className="text-xs text-purple-600">Total Spent</div>
                  </div>
                  <div className="bg-orange-50 p-3 rounded-lg">
                    <div className="font-bold text-orange-600">{selectedMember.lastVisit || 'Never'}</div>
                    <div className="text-xs text-orange-600">Last Visit</div>
                  </div>
                </div>
              </div>
            </div>
            
            <div className="p-6 border-t bg-gray-50">
              <div className="flex justify-end space-x-3">
                <button
                  onClick={() => setShowMemberDetails(false)}
                  className="px-4 py-2 text-gray-600 border border-gray-300 rounded-lg hover:bg-gray-100 transition-colors"
                >
                  Close
                </button>
                <button className="px-4 py-2 bg-orange-500 text-white rounded-lg hover:bg-orange-600 transition-colors">
                  Edit Member
                </button>
              </div>
            </div>
          </div>
        </div>
      )}
    </div>
  );
};

export default MembershipManagementSystem;
