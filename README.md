# ronifhs.github.io
import React, { useState, useEffect } from 'react'; import { Card, CardContent } from '@/components/ui/card'; import { Button } from '@/components/ui/button';

export default function TrainWatcher() { const [origin, setOrigin] = useState(''); const [destination, setDestination] = useState(''); const [date, setDate] = useState(''); const [status, setStatus] = useState('Not checking'); const [ticketsFound, setTicketsFound] = useState(false); const [intervalId, setIntervalId] = useState(null);

useEffect(() => { if (ticketsFound && Notification.permission === 'granted') { new Notification('🚆 Ticket Found!', { body: Tickets available from ${origin} to ${destination} on ${date}, }); } }, [ticketsFound]);

const checkTickets = async () => { setStatus('Checking for tickets...'); try { const response = await fetch('/api/check-ticket', {

