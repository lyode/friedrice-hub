import React, { useState } from 'react';
import { Users, Calendar, Bell, Star, Plus, Search, Edit, Phone, Mail, MapPin, TrendingUp, Award, AlertCircle, Download, CheckCircle, Clock, Gift, CreditCard } from 'lucide-react';

const MembershipManagementSystem = () => {
  const [activeTab, setActiveTab] = useState('activation');
  const [searchTerm, setSearchTerm] = useState('');
  const [selectedMember, setSelectedMember] = useState(null);
  const [showMemberDetails, setShowMemberDetails] = useState(false);

  const [members, setMembers] = useState([
    {
      id: 'M001', name: 'Sarah Chen', phone: '+60123456789', email: 'sarah@email.com',
      address: 'Shah Alam, Selangor', joinDate: '2024-01-15', expiryDate: '2025-01-15',
      duration: '12 months', membershipFee: 250, status: 'Active', points: 450,
      visits: 12, totalSpent: 480.50, lastVisit: '2024-06-10'
    },
    {
      id: 'M002', name: 'Ahmad Rahman', phone: '+60198765432', email: 'ahmad@email.com',
      address: 'Petaling Jaya, Selangor', joinDate: '2024-02-20', expiryDate: '2025-02-20',
      duration: '12 months', membershipFee: 250, status: 'Expiring Soon', points: 280,
      visits: 8, totalSpent: 320.00, lastVisit: '2024-06-05'
    },
    {
      id: 'M003', name: 'Priya Sharma', phone: '+60167890123', email: 'priya@email.com',
      address: 'Subang Jaya, Selangor', joinDate: '2024-03-10', expiryDate: '2025-09-10',
      duration: '18 months', membershipFee: 375, status: 'Active', points: 150,
      visits: 5, totalSpent: 180.00, lastVisit: '2024-06-12'
    }
  ]);

  const [newMember, setNewMember] = useState({
    name: '', phone: '', email: '', address: '', duration: '12'
  });

  const getMembershipFee = (duration) => {
    const fees = { '1': 30, '3': 80, '6': 150, '12': 250, '18': 375, '24': 500 };
    return fees[duration] || 0;
  };

  const addNewMember = () => {
    if (newMember.name && newMember.phone) {
      const memberId = `M${String(members.length + 1).padStart(3, '0')}`;
      const today = new Date();
      const expiry = new Date(today);
      expiry.setMonth(expiry.getMonth() + parseInt(newMember.duration));

      const member = {
        id: memberId, name: newMember.name, phone: newMember.phone,
        email: newMember.email, address: newMember.address,
        joinDate: today.toISOString().split('T')[0],
        expiryDate: expiry.toISOString().split('T')[0],
        duration: `${newMember.duration} months`,
        membershipFee: getMembershipFee(newMember.duration),
        status: 'Active', points: 0, visits: 0, totalSpent: 0, lastVisit: null
      };

      setMembers([...members, member]);
      setNewMember({ name: '', phone: '', email: '', address: '', duration: '12' });
    }
  };

  const getStatusColor = (status) => {
    switch(status) {
      case 'Active': return 'bg-green-100 text-green-800';
      case 'Expiring Soon': return 'bg-yellow-100 text-yellow-800';
      case 'Expired': return 'bg-red-100 text-red-800';
      default: return 'bg-gray-100 text-gray-800';
    }
  };

  const getDaysToExpiry = (expiryDate) => {
    const today = new Date();
    const expiry = new Date(expiryDate);
    const diffTime = expiry - today;
    return Math.ceil(diffTime / (1000 * 60 * 60 * 24));
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
        return { ...member, expiryDate: newExpiry.toISOString().split('T')[0], status: 'Active' };
      }
      return member;
    }));
  };

  const totalMembers = members.length;
  const activeMembers = members.filter(m => m.status === 'Active').length;
  const totalRevenue = members.reduce((sum, m) => sum + m.totalSpent, 0);

  return (
    <div className="w-full min-h-screen bg-gray-50">
      <div className="max-w-7xl mx-auto p-3 sm:p-4 lg:p-6">
        {/* Header */}
        <div className="bg-gradient-to-r from-orange-500 to-red-500 rounded-lg shadow-lg p-4 sm:p-6 mb-4 sm:mb-6 text-white">
          <h1 className="text-xl sm:text-2xl lg:text-3xl font-bold mb-2">🍚 Fried Rice Shop</h1>
          <h2 className="text-lg sm:text-xl font-semibold mb-2">Membership Management</h2>
          <p className="text-orange-100 text-sm">Activate, track, and manage your customer memberships</p>
          
          {/* Stats */}
          <div className="grid grid-cols-2 lg:grid-cols-4 gap-3 mt-4">
            <div className="bg-white bg-opacity-20 rounded-lg p-3 text-center">
              <div className="text-xl font-bold">{totalMembers}</div>
              <div className="text-xs text-orange-100">Total Members</div>
            </div>
            <div className="bg-white bg-opacity-20 rounded-lg p-3 text-center">
              <div className="text-xl font-bold">{activeMembers}</div>
              <div className="text-xs text-orange-100">Active Members</div>
            </div>
            <div className="bg-white bg-opacity-20 rounded-lg p-3 text-center">
              <div className="text-xl font-bold">RM{totalRevenue.toFixed(0)}</div>
              <div className="text-xs text-orange-100">Total Revenue</div>
            </div>
            <div className="bg-white bg-opacity-20 rounded-lg p-3 text-center">
              <div className="text-xl font-bold">{expiringMembers.length}</div>
              <div className="text-xs text-orange-100">Expiring Soon</div>
            </div>
          </div>
        </div>

        {/* Tabs */}
        <div className="bg-white rounded-lg shadow-md mb-6">
          <div className="flex border-b overflow-x-auto">
            {['activation', 'tracking', 'renewals', 'analytics'].map((tab) => (
              <button
                key={tab}
                onClick={() => setActiveTab(tab)}
                className={`px-4 py-3 font-medium text-sm flex items-center ${activeTab === tab 
                  ? 'border-b-2 border-orange-500 text-orange-600' 
                  : 'text-gray-500 hover:text-gray-700'}`}
              >
                {tab === 'activation' && <Users className="w-4 h-4 mr-2" />}
                {tab === 'tracking' && <Calendar className="w-4 h-4 mr-2" />}
                {tab === 'renewals' && <Bell className="w-4 h-4 mr-2" />}
                {tab === 'analytics' && <TrendingUp className="w-4 h-4 mr-2" />}
                {tab.charAt(0).toUpperCase() + tab.slice(1)}
                {tab === 'renewals' && ` (${expiringMembers.length})`}
              </button>
            ))}
          </div>

          {/* Activation Tab */}
          {activeTab === 'activation' && (
            <div className="p-6">
              <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div>
                  <h2 className="text-xl font-bold text-gray-800 mb-6">New Member Registration</h2>
                  <div className="space-y-4">
                    <input
                      type="text"
                      placeholder="Full Name *"
                      value={newMember.name}
                      onChange={(e) => setNewMember({...newMember, name: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500"
                    />
                    <input
                      type="text"
                      placeholder="Phone Number *"
                      value={newMember.phone}
                      onChange={(e) => setNewMember({...newMember, phone: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500"
                    />
                    <input
                      type="email"
                      placeholder="Email (Optional)"
                      value={newMember.email}
                      onChange={(e) => setNewMember({...newMember, email: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500"
                    />
                    <input
                      type="text"
                      placeholder="Address (Optional)"
                      value={newMember.address}
                      onChange={(e) => setNewMember({...newMember, address: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500"
                    />
                    <select
                      value={newMember.duration}
                      onChange={(e) => setNewMember({...newMember, duration: e.target.value})}
                      className="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-orange-500"
                    >
                      <option value="1">1 Month - RM30</option>
                      <option value="3">3 Months - RM80</option>
                      <option value="6">6 Months - RM150</option>
                      <option value="12">12 Months - RM250 (Most Popular)</option>
                      <option value="18">18 Months - RM375</option>
                      <option value="24">24 Months - RM500</option>
                    </select>
                    <button
                      onClick={addNewMember}
                      disabled={!newMember.name || !newMember.phone}
                      className="w-full bg-orange-500 hover:bg-orange-600 disabled:bg-gray-300 text-white py-3 px-4 rounded-lg font-medium flex items-center justify-center"
                    >
                      <Plus className="w-4 h-4 mr-2" />
                      Activate Membership - RM{getMembershipFee(newMember.duration)}
                    </button>
                  </div>
                </div>

                <div>
                  <h2 className="text-xl font-bold text-gray-800 mb-6">Membership Pricing</h2>
                  <div className="bg-orange-50 border rounded-lg p-6">
                    <div className="flex items-center mb-4">
                      <Award className="w-6 h-6 text-orange-500 mr-3" />
                      <h3 className="font-semibold text-lg">Fried Rice Club Member</h3>
                    </div>
                    <div className="space-y-3">
                      {[
                        { months: '1 Month', price: 'RM30' },
                        { months: '3 Months', price: 'RM80' },
                        { months: '6 Months', price: 'RM150' },
                        { months: '12 Months', price: 'RM250', popular: true },
                        { months: '18 Months', price: 'RM375' },
                        { months: '24 Months', price: 'RM500' }
                      ].map((item, index) => (
                        <div key={index} className={`grid grid-cols-2 gap-4 p-3 rounded-lg border ${item.popular ? 'bg-green-50 border-green-200' : 'bg-white'}`}>
                          <div className="font-medium">
                            {item.months}
                            {item.popular && <span className="block text-xs text-green-600">Most Popular</span>}
                          </div>
                          <div className={`font-bold ${item.popular ? 'text-green-600' : 'text-orange-600'}`}>
                            {item.price}
                          </div>
                        </div>
                      ))}
                    </div>
                  </div>
                </div>
              </div>
            </div>
          )}

          {/* Tracking Tab */}
          {activeTab === 'tracking' && (
            <div className="p-6">
              <div className="flex justify-between items-center mb-6">
                <h2 className="text-xl font-bold">All Members ({filteredMembers.length})</h2>
                <div className="flex items-center space-x-4">
                  <div className="relative">
                    <Search className="w-4 h-4 absolute left-3 top-3 text-gray-400" />
                    <input
                      type="text"
                      placeholder="Search members..."
                      value={searchTerm}
                      onChange={(e) => setSearchTerm(e.target.value)}
                      className="pl-10 pr-4 py-2 border rounded-lg focus:ring-2 focus:ring-orange-500"
                    />
                  </div>
                  <button className="bg-green-500 text-white px-4 py-2 rounded-lg text-sm font-medium flex items-center">
                    <Download className="w-4 h-4 mr-2" />Export
                  </button>
                </div>
              </div>

              <div className="overflow-x-auto">
                <table className="w-full bg-white rounded-lg shadow">
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
                      return (
                        <tr key={member.id} className="border-t hover:bg-gray-50">
                          <td className="p-4">
                            <div className="font-medium text-gray-800">{member.name}</div>
                            <div className="text-sm text-gray-500">{member.id}</div>
                          </td>
                          <td className="p-4">
                            <div className="text-sm text-gray-600 flex items-center">
                              <Phone className="w-3 h-3 mr-1" />{member.phone}
                            </div>
                            {member.email && (
                              <div className="text-sm text-gray-600 flex items-center">
                                <Mail className="w-3 h-3 mr-1" />{member.email}
                              </div>
                            )}
                          </td>
                          <td className="p-4">
                            <span className={`px-3 py-1 rounded-full text-xs font-medium ${getStatusColor(member.status)}`}>
                              {member.status}
                            </span>
                          </td>
                          <td className="p-4">
                            <div className="text-sm">
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
                              <div className="text-xs text-gray-500">
                                {daysToExpiry > 0 ? `${daysToExpiry} days left` : 'Expired'}
                              </div>
                            </div>
                          </td>
                          <td className="p-4">
                            <button
                              onClick={() => {
                                setSelectedMember(member);
                                setShowMemberDetails(true);
                              }}
                              className="text-blue-600 hover:text-blue-800 p-1"
                            >
                              <Edit className="w-4 h-4" />
                            </button>
                          </td>
                        </tr>
                      );
                    })}
                  </tbody>
                </table>
              </div>
            </div>
          )}

          {/* Renewals Tab */}
          {activeTab === 'renewals' && (
            <div className="p-6">
              <h2 className="text-xl font-bold mb-6">Membership Renewal Alerts</h2>
              {expiringMembers.length === 0 ? (
                <div className="text-center py-12">
                  <CheckCircle className="w-16 h-16 text-green-500 mx-auto mb-4" />
                  <h3 className="text-lg font-medium text-gray-800 mb-2">All Good!</h3>
                  <p className="text-gray-600">No memberships expiring in the next 30 days.</p>
                </div>
              ) : (
                <div className="space-y-4">
                  {expiringMembers.map((member) => {
                    const daysToExpiry = getDaysToExpiry(member.expiryDate);
                    return (
                      <div key={member.id} className="bg-white border border-yellow-200 rounded-lg p-6">
                        <div className="flex items-center justify-between mb-4">
                          <div className="flex items-center space-x-4">
                            <div className="w-10 h-10 bg-yellow-100 rounded-full flex items-center justify-center">
                              <Clock className="w-5 h-5 text-yellow-600" />
                            </div>
                            <div>
                              <h3 className="font-semibold text-lg">{member.name}</h3>
                              <div className="text-sm text-gray-600">{member.phone}</div>
                            </div>
                          </div>
                          <div className="text-right">
                            <div className="text-lg font-bold text-yellow-600">{daysToExpiry} days</div>
                            <div className="text-xs text-gray-500">until expiry</div>
                          </div>
                        </div>
                        <div className="flex space-x-2">
                          <button className="bg-yellow-500 text-white px-4 py-2 rounded-lg text-sm font-medium flex items-center">
                            <Bell className="w-4 h-4 mr-2" />Send Reminder
                          </button>
                          <button 
                            onClick={() => renewMembership(member.id, 12)}
                            className="bg-green-500 text-white px-4 py-2 rounded-lg text-sm font-medium flex items-center"
                          >
                            <CheckCircle className="w-4 h-4 mr-2" />Renew 12 Months
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
              <h2 className="text-xl font-bold mb-6">Membership Analytics</h2>
              <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
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
                      <p className="text-2xl font-bold">RM{(totalRevenue/totalMembers).toFixed(2)}</p>
                    </div>
                    <CreditCard className="w-8 h-8 text-purple-200" />
                  </div>
                </div>
                <div className="bg-gradient-to-r from-orange-500 to-orange-600 text-white p-6 rounded-lg">
                  <div className="flex items-center justify-between">
                    <div>
                      <p className="text-orange-100">Renewals Due</p>
                      <p className="text-2xl font-bold">{expiringMembers.length}</p>
                    </div>
                    <Bell className="w-8 h-8 text-orange-200" />
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
                  <h3 className="text-xl font-bold">Member Details</h3>
                  <button
                    onClick={() => setShowMemberDetails(false)}
                    className="text-gray-500 hover:text-gray-700 text-2xl"
                  >
                    ×
                  </button>
                </div>
              </div>
              <div className="p-6">
                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div>
                    <h4 className="font-semibold mb-3">Personal Information</h4>
                    <div className="space-y-2 text-sm">
                      <div><strong>ID:</strong> {selectedMember.id}</div>
                      <div><strong>Name:</strong> {selectedMember.name}</div>
                      <div><strong>Phone:</strong> {selectedMember.phone}</div>
                      <div><strong>Email:</strong> {selectedMember.email || 'Not provided'}</div>
                      <div><strong>Address:</strong> {selectedMember.address || 'Not provided'}</div>
                    </div>
                  </div>
                  <div>
                    <h4 className="font-semibold mb-3">Membership Details</h4>
                    <div className="space-y-2 text-sm">
                      <div><strong>Join Date:</strong> {selectedMember.joinDate}</div>
                      <div><strong>Expiry Date:</strong> {selectedMember.expiryDate}</div>
                      <div><strong>Duration:</strong> {selectedMember.duration}</div>
                      <div><strong>Fee:</strong> RM{selectedMember.membershipFee}</div>
                      <div><strong>Status:</strong> 
                        <span className={`ml-2 px-2 py-1 rounded-full text-xs font-medium ${getStatusColor(selectedMember.status)}`}>
                          {selectedMember.status}
                        </span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div className="p-6 border-t bg-gray-50">
                <div className="flex justify-end space-x-3">
                  <button
                    onClick={() => setShowMemberDetails(false)}
                    className="px-4 py-2 text-gray-600 border border-gray-300 rounded-lg hover:bg-gray-100"
                  >
                    Close
                  </button>
                  <button className="px-4 py-2 bg-orange-500 text-white rounded-lg hover:bg-orange-600">
                    Edit Member
                  </button>
                </div>
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
};

export default MembershipManagementSystem;
