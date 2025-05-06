import { useState } from 'react';
import { claims } from '../data';

// Add this inside the Claims component before the return statement
const [newClaim, setNewClaim] = useState({
  policyId: '',
  triggerEvent: '',
  details: ''
});

const handleSubmit = (e: React.FormEvent) => {
  e.preventDefault();
  const claim: ClaimHistory = {
    id: `CL-00${claims.length + 1}`,
    policyId: newClaim.policyId,
    date: new Date().toISOString().split('T')[0],
    amount: Math.floor(Math.random() * 5000) + 1000, // Example amount
    status: 'pending',
    triggerEvent: newClaim.triggerEvent
  };
  claims.push(claim);
  setNewClaim({ policyId: '', triggerEvent: '', details: '' });
  alert('Claim submitted successfully!');
};
